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
  - "[[constant-propagation]]"
---

# Dead Code Elimination

Dead code elimination removes code that is guaranteed to never execute. In a sense, most optimizations remove redundant code, but this one specifically targets unreachable branches.

Example: if `f(x)` returns `x * 2`, then in `if f(5) % 2 == 0 { ... } else { ... }`, the else-branch is dead code and can be removed, since `f(5)` is always 10, which is always even.

The general problem of determining which code is dead is undecidable, but the compiler handles many practical cases through [[constant-folding]] and [[constant-propagation]].

## Prerequisites

- [[constant-folding]] — Constant folding reveals which branches are dead
- [[constant-propagation]] — Propagating constants enables the compiler to determine unreachable code

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[constant-folding]]
- [[constant-propagation]]
- [[common-subexpression-elimination]]
- [[link-time-optimization]]
