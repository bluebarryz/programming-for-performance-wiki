---
tags:
  - concept
  - ece459
  - performance
  - memory
lectures:
  - L17
prerequisites:
  - "[[simd]]"
  - "[[memory-hierarchy]]"
---

# Data Layout and Alignment

Rust generally aligns primitives to their sizes (e.g., `i32` is 4-byte aligned). On some architectures (ARM Cortex), alignment has performance implications; on x86, less so.

Under the default representation, Rust makes no guarantees about struct layout beyond alignment. You can use:

- `repr(packed(N))` to reduce alignment (and struct size), at a potential performance cost
- `repr(align(N))` to increase alignment for SIMD or cache-line purposes
- `repr(C)` to get a C-compatible, predictable layout

These directives give more control over data layout, which matters when using [[simd]] instructions that require or benefit from aligned memory access.

Using smaller data types (e.g., `i16` instead of `i32`) can halve memory usage and double the number of elements processed per [[simd]] instruction. The trade-off is reduced range and potentially more complex arithmetic (bit shifting for packed operations).

## Prerequisites

- [[simd]] — Alignment matters because SIMD instructions require or benefit from aligned memory access
- [[memory-hierarchy]] — Understanding cache lines and memory access patterns motivates alignment choices

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[simd]]
- [[sse-and-avx]]
- [[stream-vbyte]]
