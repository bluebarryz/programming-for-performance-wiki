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

## Examples

### Fusion — reducing loop overhead

```rust
// Before: two loops, two sets of branch/counter operations
for i in 0..1000 { a[i] = b[i] + 1; }
for i in 0..1000 { c[i] = b[i] * 2; }

// After: one loop, b[i] loaded once per iteration instead of twice
for i in 0..1000 {
    a[i] = b[i] + 1;
    c[i] = b[i] * 2;
}
```

Fusion also lets the compiler reuse `b[i]` already in a register across both statements.

### Fission — improving cache locality

```rust
// Before: one loop touching a, b, c, d — large working set, more cache pressure
for i in 0..1000 {
    a[i] = b[i] + 1;
    c[i] = d[i] * 2;
}

// After: two loops, each with a smaller working set that fits in cache
for i in 0..1000 { a[i] = b[i] + 1; }
for i in 0..1000 { c[i] = d[i] * 2; }
```

Useful when `a`, `b`, `c`, `d` are all large — splitting keeps each loop's footprint small enough to stay in L1/L2 cache.

## Prerequisites

- [[loop-optimizations]] — Fusion and fission are specific loop optimization transformations
- [[cache-misses]] — Fission improves cache behaviour by reducing working set per loop

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-optimizations]]
- [[loop-interchange]]
- [[loop-invariant-code-motion-aka-hoisting]]
