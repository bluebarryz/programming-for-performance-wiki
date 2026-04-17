---
tags:
  - concept
  - ece459
  - performance
  - compiler
  - simd
lectures:
  - L17
prerequisites:
  - "[[simd]]"
  - "[[sse-and-avx]]"
---

# Auto-Vectorization

Auto-vectorization is the compiler's automatic use of [[simd]] instructions when it knows the target architecture supports them. For example, compiling a simple loop that adds two slices element-wise with `rustc` defaults produces scalar SSE2 instructions (`movsd`, `addsd`). Adding `-O` causes the compiler to emit packed variants (`movupd`, `addpd`) that process two elements per iteration.

This is a "piece of good news" -- the compiler does this for free. The compiler also generates fallback code for edge cases (e.g., odd numbers of elements).

Note that optimization level `"z"` (optimize for binary size) turns off loop vectorization. The `native` target CPU option enables the best SIMD instructions available on the build machine.

## Prerequisites

- [[simd]] — Auto-vectorization is the compiler's automatic use of SIMD instructions
- [[sse-and-avx]] — The specific instruction sets the compiler targets when auto-vectorizing

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[simd]]
- [[sse-and-avx]]
- [[compiler-optimization-levels]]
- [[loop-unrolling]]
