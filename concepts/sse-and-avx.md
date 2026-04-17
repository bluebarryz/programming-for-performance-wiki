---
tags:
  - concept
  - ece459
  - performance
  - hardware
  - simd
lectures:
  - L17
prerequisites:
  - "[[simd]]"
---

# SSE and AVX

SSE (Streaming SIMD Extensions) and AVX (Advanced Vector Extensions) are x86 instruction set extensions that implement [[simd]] operations.

## Key Details

- SSE2 provides 128-bit XMM registers (e.g., `xmm0`). Instructions like `movsd`/`addsd` operate on scalar doubles (64-bit), while packed variants like `movupd`/`addpd` operate on two doubles simultaneously.
- With optimization (`-O`), the Rust/LLVM compiler can automatically emit packed instructions from scalar loop code, halving the number of loop iterations.
- The `target` compiler parameter controls which instruction set extensions are available. Choosing a newer architecture (e.g., with AVX) enables wider registers but may fail on older machines.
- The `sd` suffix denotes scalar double; the `p` prefix (e.g., `addpd`) denotes packed operations on multiple data elements at once.

## Prerequisites

- [[simd]] — SSE and AVX are x86 instruction set implementations of SIMD

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[simd]]
- [[auto-vectorization]]
- [[data-layout-and-alignment]]
