---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites: []
---

# Constant Folding

Constant folding is the simplest compiler optimization: evaluate constant expressions at compile time instead of runtime. Tag line: "Why do later something you can do now?"

Example: `i = 1024 * 1024` becomes `i = 1048576`. The compiler will not emit code to perform the multiplication at runtime.

Enabled **always** (at all optimization levels).

## Prerequisites

None — foundational concept.

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[constant-propagation]]
- [[common-subexpression-elimination]]
- [[dead-code-elimination]]
- [[compiler-optimization-levels]]
