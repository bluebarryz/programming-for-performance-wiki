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

### Function pointers (C)

```c
void (*fn)(void) = flip ? foo : bar;
fn();
```

The call site `fn()` has no static target. The compiler must use pointer analysis to determine that `fn ∈ {foo, bar}`, adding both as potential callees. Without this, it must conservatively assume `fn` could call anything.

### Virtual dispatch (C++)

```c++
struct Animal { virtual void speak() = 0; };
struct Dog : Animal { void speak() override { ... } };
struct Cat : Animal { void speak() override { ... } };

void make_speak(Animal *a) { a->speak(); }
```

The call `a->speak()` could resolve to `Dog::speak` or `Cat::speak`. A precise call graph requires knowing the possible dynamic types of `a` — this is where alias/points-to analysis pays off. An imprecise graph includes all overrides of `speak`, hurting devirtualization.

### Dynamic dispatch (Rust)

```rust
fn make_sound(animal: &dyn Animal) { animal.speak(); }
```

`dyn Animal` is a fat pointer (data ptr + vtable ptr). The call graph edge is through the vtable, so the compiler needs to track which concrete types flow into `make_sound` to resolve the callee. Static dispatch via generics (`impl Animal`) avoids this entirely.

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
