---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[borrowing-and-references]]"
  - "[[common-subexpression-elimination]]"
---

# Alias and Pointer Analysis

**Aliasing** occurs when two different variables refer to the same memory location. For example, if `int *p` and `int *q` both point to the same address, writing through `p` silently changes what you read through `q`. This makes it impossible to reason about a variable's value in isolation.

Alias analysis determines whether two variables (typically pointers or references) refer to the same memory location. Pointer analysis abstractly tracks which regions of the heap each variable points to, where a region may be the memory allocated at a particular program point. Compiler optimizations frequently need to know what parts of memory each statement accesses -- things like "neither x nor y change" -- and alias analysis provides this information.

When two pointers are known not to alias, their effects are independent, making it safe to reorder operations, eliminate redundant loads, or perform other transformations. This also helps in reasoning about side effects. In C, scalar optimizations become much more complicated in the presence of pointers and arrays because they can alias freely. Rust's borrowing system primarily controls aliasing, which makes automatic parallelization much more tractable. Shape analysis builds on pointer analysis to determine whether data structures are trees rather than lists.

Alias and pointer analysis is foundational to interprocedural optimization. Accurate results feed into [[call-graphs]], [[inlining]], [[devirtualization]], and [[constant-propagation]] across function boundaries. Without good alias information, the compiler must conservatively assume that any pointer write could affect any pointer read, severely limiting optimization opportunities.

## Examples

### Aliasing blocks optimization

```c
void add(int *a, int *b, int *c) {
    *a += *c;
    *b += *c;
}
```

The compiler cannot cache `*c` across the two additions — if `a == c`, the first line changes `*c`, so the second read must reload from memory. With the `restrict` keyword (`int *restrict c`), the programmer asserts no aliasing, allowing the compiler to hoist the load.

### Loop vectorization blocked by aliasing

```c
void scale(float *out, float *in, float k, int n) {
    for (int i = 0; i < n; i++)
        out[i] = in[i] * k;
}
```

The compiler cannot vectorize this loop (e.g. using SIMD) without knowing `out` and `in` don't overlap. If `out = in + 1`, iteration `i` writes `out[i]`, which is `in[i+1]`, corrupting the next iteration's input. The compiler must emit a scalar loop or generate a runtime overlap check. With `float *restrict out`, overlap is ruled out and vectorization is safe.

### Dead store elimination blocked by aliasing

```c
void init(int *x, int *log) {
    *x = 0;
    *log = 1;
    *x = 42;
}
```

The first write `*x = 0` looks like a dead store — it is immediately overwritten by `*x = 42`. But if `x == log`, the write to `*log` also changes `*x`, so the first store is not dead. The compiler must keep all three stores unless it can prove `x != log`.

### Constant propagation blocked by aliasing

```c
int compute(int *a, int *b) {
    *a = 10;
    side_effect(b);     // might write through b, which could equal a
    return *a + 1;
}
```

Even though `*a` was just set to `10`, the compiler cannot substitute `return 11` — `side_effect` receives `b`, and if `b == a`, it may overwrite `*a`. The load of `*a` after the call cannot be eliminated.

### Pointer analysis: heap regions

```c
int *p = malloc(...);  // region R1
int *q = malloc(...);  // region R2
int *r = p;
```

Points-to sets: `p → {R1}`, `q → {R2}`, `r → {R1}`. Since `q` and `r` point to disjoint regions, a write through `q` cannot affect a read through `r` — safe to reorder.

### Rust eliminates the problem

```rust
fn add(a: &mut i32, c: &i32) {
    *a += *c;
}
```

The borrow checker guarantees `a` and `c` are distinct references, so the compiler can freely cache `*c` without any analysis — aliasing is ruled out by construction.

Rust enforces two complementary rules:
- **Ownership:** exactly one owner at a time. When the owner goes out of scope, the memory is freed.
- **Borrowing (shared XOR mutable):** you may have either many `&T` (shared/immutable) references, or exactly one `&mut T` (exclusive/mutable) reference — never both simultaneously.

Because `a: &mut i32` is live, the borrow checker rejects any call site that passes the same address as `c: &i32`. Aliasing is structurally impossible, so no runtime analysis is needed.

### Shape analysis: tree vs. list

```c
node->left->parent = node;   // could form a cycle
```

Pointer analysis alone cannot determine if a structure is a DAG or tree. Shape analysis tracks structural invariants (e.g., "each node has at most one predecessor") to confirm a data structure is a tree, enabling tree-specific optimizations.

## Prerequisites

- [[borrowing-and-references]] — Rust's borrowing system controls aliasing, making analysis more tractable
- [[common-subexpression-elimination]] — Alias analysis enables CSE by proving memory locations are independent

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[call-graphs]]
- [[inlining]]
- [[link-time-optimization]]
- [[devirtualization]]
- [[common-subexpression-elimination]]
