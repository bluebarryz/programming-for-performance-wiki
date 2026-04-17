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
---

# Loop-Invariant Code Motion (aka hoisting)

Also known as **loop hoisting**, this optimization moves calculations that don't change across iterations out of the loop.

Example:
```rust
// Before                      // After
for i in 0..100 {              s = x * y;
    s = x * y;                 for i in 0..100 {
    a[i] = s * i;                  a[i] = s * i;
}                              }
```

This reduces the work done per iteration. It is safe when the hoisted expression has no side effects and its operands don't change within the loop.

## Prerequisites

- [[loop-optimizations]] — Loop-invariant code motion is a specific loop optimization technique

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-optimizations]]
- [[induction-variable-elimination]]
- [[loop-fusion-and-fission]]
