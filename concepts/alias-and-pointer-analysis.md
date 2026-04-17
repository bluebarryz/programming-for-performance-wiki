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
