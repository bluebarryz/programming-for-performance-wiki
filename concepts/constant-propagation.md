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

# Constant Propagation

Constant propagation moves constant values from their definition to their use. It is valid when there are no redefinitions of the variable between definition and use.

Example: given `let w = 3; ... let z = w + y;`, the compiler can propagate the constant 3, yielding `z = 3 + y`.

Often combined with [[copy-propagation]] for greater effect. In C, these optimizations are complicated by pointers (e.g., `z = *w + y`). In Rust, the LLVM backend does not fully exploit Rust's uniqueness/borrowing guarantees for these optimizations.

## Prerequisites

- [[constant-folding]] — Propagated constants enable further constant folding

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[copy-propagation]]
- [[constant-folding]]
- [[common-subexpression-elimination]]
- [[dead-code-elimination]]
