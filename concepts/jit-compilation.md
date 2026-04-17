---
tags:
  - concept
  - ece459
  - runtime-optimization
lectures:
  - L20
prerequisites:
  - "[[compiler-optimization-levels]]"
  - "[[inlining]]"
  - "[[observe-and-change]]"
---

# JIT Compilation

Just-in-time (JIT) compilation is a technique where code is compiled from an intermediate representation (such as Java bytecode) into native machine code at runtime, rather than ahead of time. In the JVM, the original program is first compiled by the Java compiler into bytecode, and then the JIT compiler gets a "second chance" at optimization during execution.

Oracle's HotSpot JVM includes two JIT compilers: a client compiler that produces output quickly but with less optimization, and a server compiler that takes more time and resources to produce more efficient code. This distinction exists because clients pay startup costs more frequently, so fast compilation is prioritized, while servers run for long periods and benefit from higher-quality code generation.

The major advantage of JIT compilation over ahead-of-time compilation is the ability to observe actual runtime behavior and change optimization decisions accordingly. If the original compile-time decision not to inline a function turns out to be wrong, the JIT compiler can reverse that decision after observing that the function is called frequently. This adaptive approach enables optimizations like [[escape-analysis]], [[on-stack-replacement]], [[lock-elision-and-coarsening]], and the use of [[intrinsics]]. Rust does not have JIT compilation because it chose not to include a managed runtime like the JVM -- the tradeoff is less runtime overhead but no ability to re-optimize based on observed behavior.

## Prerequisites

- [[compiler-optimization-levels]] — JIT compilation gets a "second chance" at optimizations that ahead-of-time compilers make at fixed levels
- [[inlining]] — JIT can reverse compile-time inlining decisions based on observed runtime behavior
- [[observe-and-change]] — JIT compilation embodies the observe-and-change principle by adapting code at runtime

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[escape-analysis]]
- [[on-stack-replacement]]
- [[intrinsics]]
- [[lock-elision-and-coarsening]]
- [[binary-rewriting]]
