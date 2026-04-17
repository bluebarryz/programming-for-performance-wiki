---
tags:
  - concept
  - ece459
  - performance
  - parallelism
  - hardware
lectures:
  - L17
prerequisites:
  - "[[data-parallelism]]"
  - "[[instruction-level-parallelism]]"
  - "[[pipelining]]"
---

# SIMD (Single Instruction Multiple Data)

SIMD is a form of [[data-parallelism]] at the instruction level. Each SIMD instruction operates on an entire vector of data simultaneously, using a single control unit to command multiple processing units. This reduces overhead in the instruction stream compared to processing elements one at a time (SISD -- Single Instruction Single Data).

SIMD originated with supercomputers in the 1970s. Modern implementations include x86 [[sse-and-avx]] instructions, SPARC VIS, and Power/PowerPC AltiVec.

## Advantages

- Reduces loop iteration count (e.g., processing 2 or 4 elements per iteration instead of 1)
- Complementary to threads -- no thread startup overhead, uses registers instead of shared memory
- More efficient than multicore for applicable workloads: uses less CPU resources (cores and power) and runs faster (per Daniel Lemire)

## Limitations

- All processing units must do the same thing -- not suitable when different elements need different operations
- Diminishing returns with more processing units (less likely to have enough identical operations)

## Using SIMD in Rust

1. **Automatic**: the compiler can auto-vectorize loops when targeting an architecture that supports it (see [[auto-vectorization]])
2. **Explicit libraries**: crates like `simdeez` provide lightweight wrappers around SIMD intrinsics with runtime dispatch across scalar, SSE2, SSE4.1, and AVX

## Prerequisites

- [[data-parallelism]] — SIMD is hardware-level data parallelism, applying one instruction to multiple data elements
- [[instruction-level-parallelism]] — SIMD extends the processor's ability to do more work per cycle
- [[pipelining]] — Understanding how instructions flow through the processor helps explain SIMD's efficiency

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[data-parallelism]]
- [[sse-and-avx]]
- [[auto-vectorization]]
- [[stream-vbyte]]
- [[data-layout-and-alignment]]
