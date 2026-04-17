---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[call-graphs]]"
  - "[[inlining]]"
---

# Tail Recursion Elimination

Tail recursion elimination is a compiler optimization that replaces a recursive function call in tail position (the last operation before returning) with a jump back to the beginning of the function, effectively converting recursion into iteration. This avoids function call overhead and, critically, prevents call stack growth, which would otherwise lead to stack overflow for deep recursions.

A function call is in "tail position" when there is no further work to do after the recursive call returns. For example, in a Fibonacci implementation using an accumulator pattern, the recursive call `fibonacci_lr(n - 1, a + b, a)` is the last thing the function does, so the current stack frame can be reused. This optimization is mandatory in some functional languages (like Scheme) but is not guaranteed in C, C++, or Rust. In Rust, LLVM may or may not perform the transformation depending on optimization level and the specific code pattern.

The practical benefit is turning an O(n) stack space algorithm into O(1) stack space while preserving the recursive coding style. This is one of the interprocedural optimizations that benefits from [[call-graphs]] and is related to [[inlining]] in that both transform function call boundaries to reduce overhead.

## Prerequisites

- [[call-graphs]] — Tail recursion elimination is an interprocedural optimization that transforms function call boundaries
- [[inlining]] — Related optimization that also reduces function call overhead

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[inlining]]
- [[call-graphs]]
- [[compiler-optimization-levels]]
- [[link-time-optimization]]
