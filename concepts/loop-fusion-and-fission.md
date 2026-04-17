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

# Loop Fusion and Fission

**Loop fusion** merges two adjacent loops with the same bounds into a single loop, reducing loop overhead:

```rust
// Before                          // After
for i in 0..100 { a[i] = 4; }     for i in 0..100 {
for i in 0..100 { b[i] = 7; }         a[i] = 4;
                                       b[i] = 7;
                                   }
```

**Loop fission** is the inverse: splitting one loop into two. This can improve data locality when the loop body accesses many different arrays and the working set doesn't fit in cache. By splitting, each loop touches fewer arrays, improving cache behaviour.

There is a trade-off between data locality (favours fission) and loop overhead (favours fusion).

## Prerequisites

- [[loop-optimizations]] — Fusion and fission are specific loop optimization transformations
- [[cache-misses]] — Fission improves cache behaviour by reducing working set per loop

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-optimizations]]
- [[loop-interchange]]
- [[loop-invariant-code-motion-aka-hoisting]]
