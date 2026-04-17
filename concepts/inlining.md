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
  - "[[cache-misses]]"
---

# Inlining

Inlining is a compiler optimization that replaces a function call with the body of the called function, inserted directly at the call site. This eliminates function call overhead (pushing/popping the stack frame, jumping) and, more importantly, enables further context-sensitive optimizations that the compiler could not perform across a function boundary.

In Rust, you can control inlining with annotations: `#[inline]` hints the compiler to inline, `#[inline(always)]` requests it unconditionally, and `#[inline(never)]` prevents it. However, inlining is merely a suggestion -- compilers may ignore the hint. In C/C++, taking the address of an inline function or using virtual functions will prevent inlining.

Inlining has a significant downside: increased program size, which can reduce instruction cache hit rates and hurt performance. Some inlines grow very rapidly, so aggressive inlining can paradoxically make programs slower. Debugging is also harder since you cannot set breakpoints in functions that no longer exist as separate entities. For library design, changing an inlined function forces all consumers to recompile -- a non-binary-compatible change. Inlining requires accurate [[call-graphs]] and is closely related to [[devirtualization]], since virtual/dynamic dispatch calls must first be resolved to concrete targets before they can be inlined.

## Prerequisites

- [[call-graphs]] — Inlining requires accurate call graphs to know what a callee does
- [[cache-misses]] — Aggressive inlining can hurt instruction cache hit rates

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[call-graphs]]
- [[devirtualization]]
- [[link-time-optimization]]
- [[tail-recursion-elimination]]
- [[alias-and-pointer-analysis]]
