---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[common-subexpression-elimination]]"
  - "[[constant-propagation]]"
---

# Copy Propagation

Copy propagation telescopes copies of variables from their definition to their use, replacing the copy with the original. It usually runs after [[common-subexpression-elimination]].

Example: after CSE produces `let y = x;`, copy propagation can replace later uses of `y` with `x`, potentially enabling further [[dead-code-elimination]] of the `y` assignment.

Combined with [[constant-propagation]], it can chain multiple simplifications: `w = 3; x = f(); y = x; z = w + y;` becomes `z = 3 + x`.

## Prerequisites

- [[common-subexpression-elimination]] — Copy propagation typically runs after CSE to telescope the copies it introduces
- [[constant-propagation]] — Combined with copy propagation for chained simplifications

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[constant-propagation]]
- [[common-subexpression-elimination]]
- [[dead-code-elimination]]
