---
tags:
  - concept
  - ece459
  - gpu
prerequisites:
  - "[[cuda]]"
---

# FP32 vs FP64

Most gaming-oriented NVIDIA GeForce GPUs do not natively support FP64 (double-precision, 64-bit floating point). Native FP64 support requires expensive datacenter GPUs. On consumer cards, FP64 operations are emulated in software and run dramatically slower than FP32 (single-precision, 32-bit) operations.

The performance difference is substantial. On the GeForce RTX 3090, FP64 runs at 1/64 the speed of FP32 (35580 vs 556 GFLOPS). AMD cards fare somewhat better, with the Radeon RX 6900 XT showing a 1/16 ratio. Using 32-bit floats instead of 64-bit doubles can yield a 16x, 32x, or even 64x speedup on consumer GPUs. For applications where full double precision is unnecessary (such as gaming or many scientific approximations), using lower-precision types is a straightforward way to trade accuracy for performance. This principle extends further: 16-bit floats can provide another approximate 2x speedup.

## Prerequisites
- [[cuda]] — FP32/FP64 performance differences are specific to GPU hardware capabilities

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[mixed-precision-training]]
- [[cuda-blocks-and-grids]]
- [[large-language-models]]
