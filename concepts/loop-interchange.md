---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[loop-optimizations]]"
  - "[[cache-misses]]"
---

# Loop Interchange

Loop interchange swaps the nesting order of loops to improve cache locality by matching the iteration order to the memory layout of array elements.

Example: Rust is row-major (`a[1][1]` is beside `a[1][2]`), so iterating over the inner dimension in the innermost loop is cache-friendly. If the original code iterates column-major, the compiler can swap the loops:

```rust
// Before: cache-unfriendly        // After: cache-friendly
for i in 0..8 {                    for j in 0..4 {
    for j in 0..4 {                    for i in 0..8 {
        a[j][i] = a[j][i] * c;            a[j][i] = a[j][i] * c;
    }                                  }
}                                  }
```

Interestingly, sometimes doing things the "wrong" way (column-major on a row-major layout) can be faster for sufficiently large matrices: it triggers all page faults up front and loads everything into cache, after which you can process freely. This has been suggested for matrix multiplication.

## Prerequisites

- [[loop-optimizations]] — Loop interchange is a specific loop optimization technique
- [[cache-misses]] — Interchange improves cache locality by matching iteration order to memory layout

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-optimizations]]
- [[loop-unrolling]]
- [[loop-fusion-and-fission]]
