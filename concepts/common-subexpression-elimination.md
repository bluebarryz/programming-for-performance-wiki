---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[constant-folding]]"
---

# Common Subexpression Elimination (CSE)

Common subexpression elimination identifies cases where the same expression `x op y` is computed more than once, and neither `x` nor `y` changes between the computations. The compiler computes it once and reuses the result.

Example: in `a = (c + d) * y; b = (c + d) * z;`, the subexpression `c + d` is computed only once.

Enabled at level 1.

## Prerequisites

- [[constant-folding]] — CSE builds on the same idea of avoiding redundant computation

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[constant-propagation]]
- [[copy-propagation]]
- [[constant-folding]]
- [[dead-code-elimination]]
