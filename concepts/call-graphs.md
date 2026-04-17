---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[alias-and-pointer-analysis]]"
---

# Call Graphs

A call graph is a directed graph showing the calling relationships between functions in a program. Many interprocedural analyses -- including [[inlining]], [[devirtualization]], and [[constant-propagation]] across function boundaries -- require accurate call graphs to determine what a callee might do (e.g., whether it modifies a particular variable).

Computing a call graph is straightforward for C-style direct function calls. It becomes much harder with virtual methods (C++, Java), C function pointers, or Rust's dynamic dispatch through trait objects (`dyn Trait`). In these cases, the compiler needs [[alias-and-pointer-analysis]] information to determine which concrete functions a call site might invoke. For Rust specifically, indirect function calls (function pointers) and dynamic dispatch through traits are the main challenges to call graph construction.

Accurate call graphs are essential for [[link-time-optimization]], where whole-program analysis must reason about the effects of functions across module boundaries. The call graph also enables dead function elimination -- if a function is never reachable from the program entry point, it can be removed entirely.

## Examples

### Direct calls (trivial)

```c
void foo() { bar(); baz(); }
void bar() {}
void baz() {}
```

Call graph: `foo → bar`, `foo → baz`. Each edge is known statically — no analysis needed.

### Inlining

```c
// math.c
int square(int x) { return x * x; }

// area.c
extern int square(int);
int area(int side) { return square(side); }
```

The call graph shows `area → square` as the only caller of `square`. Because `square` is small and this is its only call site, the compiler can inline it — replacing the call with `side * side` directly, eliminating call overhead and enabling further optimizations (e.g., constant folding if `side` is known).

**Without a call graph**, this inlining cannot happen. When compiling `area.c` in isolation, the compiler only sees `extern int square(int)` — a declaration with no body. It cannot inline what it cannot see. The call graph is what connects the call site in `area.c` to the definition in `math.c`, making the body available during [[link-time-optimization]].

Even within a single translation unit, a call graph is needed to inline safely. Consider:

```c
int square(int x) { return x * x; }
int (*fn)(int) = square;            // square's address is taken
int area(int side) { return square(side); }
```

Here `square` is reachable through both a direct call and a function pointer. The compiler must preserve `square` as a real function (with a callable address) — it cannot fully inline and delete it. The call graph makes this visible: `fn` is an indirect reference to `square`, so other code might call it at runtime. Without tracking this edge, the compiler would inline and silently break any caller going through `fn`.

### Devirtualization

```c++
struct Animal { virtual void speak() = 0; };
struct Dog : Animal { void speak() override { ... } };
struct Cat : Animal { void speak() override { ... } };

void make_speak(Animal *a) { a->speak(); }
```

The call `a->speak()` could resolve to `Dog::speak` or `Cat::speak`. If the call graph — built with alias/points-to analysis — shows that only `Dog` ever flows into `make_speak`, the virtual dispatch can be replaced with a direct call to `Dog::speak`. This eliminates vtable lookup overhead and opens the door to inlining.

Without a precise call graph, the compiler must conservatively assume any override of `speak` is a possible callee and cannot devirtualize.

### Constant propagation across calls

```c
int get_multiplier() { return 4; }
int scale(int x) { return x * get_multiplier(); }
```

The call graph shows `scale → get_multiplier`. Because `get_multiplier` always returns a constant, the compiler can propagate that value across the call edge — rewriting `scale` as `return x * 4`. This then enables further optimizations like strength reduction (replacing multiply-by-4 with a left shift).

Interprocedural constant propagation depends entirely on the call graph: the compiler must know which function is being called to reason about what it returns.

### Function pointers (C)

```c
void (*fn)(void) = flip ? foo : bar;
fn();
```

The call site `fn()` has no static target. The compiler must use pointer analysis to determine that `fn ∈ {foo, bar}`, adding both as potential callees. Without this, it must conservatively assume `fn` could call anything — blocking inlining and constant propagation through `fn`.

### Dynamic dispatch (Rust)

```rust
fn make_sound(animal: &dyn Animal) { animal.speak(); }
```

`dyn Animal` is a fat pointer (data ptr + vtable ptr). The call graph edge is through the vtable, so the compiler needs to track which concrete types flow into `make_sound` to resolve the callee. Static dispatch via generics (`impl Animal`) avoids this entirely — the call graph edge becomes direct, enabling inlining and constant propagation.

### Dead function elimination

```
main → foo → bar
            → baz
       qux          ← unreachable from main
```

`qux` has no path from `main` in the call graph, so it can be eliminated at link time (see [[link-time-optimization]]).

## Prerequisites

- [[alias-and-pointer-analysis]] — Needed to resolve indirect calls and dynamic dispatch in call graph construction

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[alias-and-pointer-analysis]]
- [[inlining]]
- [[devirtualization]]
- [[link-time-optimization]]
