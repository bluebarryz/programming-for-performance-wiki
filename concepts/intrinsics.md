---
tags:
  - concept
  - ece459
  - runtime-optimization
lectures:
  - L20
prerequisites:
  - "[[jit-compilation]]"
  - "[[simd]]"
---

# Intrinsics

Intrinsics are highly-optimized, platform-specific implementations of code, precompiled for a particular architecture (e.g., x86). In the context of JVM HotSpot optimization, if a critical piece of code has a native implementation available, the JIT compiler can substitute it for the general-purpose bytecode version, gaining a significant performance boost.

Intrinsics were originally developed in C++ rather than Java, so they operate without Java's safety guarantees. Adding a new intrinsic to the JVM is a complicated process. A newer alternative is the Graal compiler, which turns Java bytecode directly into machine code, potentially achieving similar performance benefits through a different mechanism.

The concept of intrinsics also applies outside the JVM context. In Rust and C/C++, compiler intrinsics expose specific hardware instructions (such as SIMD operations or atomic instructions) directly to the programmer, bypassing the compiler's normal code generation. This gives precise control over what instructions are emitted, which can be critical for performance-sensitive code paths where the compiler's default choices are suboptimal.

## Prerequisites

- [[jit-compilation]] — In the JVM, intrinsics are substituted by the JIT compiler for platform-specific native code
- [[simd]] — SIMD intrinsics expose specific hardware vector instructions directly to the programmer

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[jit-compilation]]
- [[escape-analysis]]
- [[on-stack-replacement]]
- [[simd]]
- [[binary-rewriting]]
