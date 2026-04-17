---
tags:
  - lecture
  - ece459
  - gpu
  - cuda
  - rust
lecture: L22
title: GPU Programming Continued
prerequisite_lectures:
  - "[[L21-GPU-Programming]]"
  - "[[L04-Rust-Breaking-the-Rules]]"
---

# L22 - GPU Programming Continued

This lecture covers the host-side code needed to launch CUDA kernels, using the RustaCUDA library to write host code in Rust. It walks through the full launch sequence: initializing the CUDA runtime, obtaining a device, creating a context, loading a module (compiled PTX), creating a stream, allocating device buffers, launching the kernel, synchronizing, and copying results back. The N-body problem is used as a concrete example, demonstrating how grid and block sizing dramatically affects performance. The lecture also covers trading floating-point precision for performance (FP32 vs FP64) on consumer GPUs.

## Prerequisite Lectures
- [[L21-GPU-Programming]] — CUDA kernel model, memory hierarchy, and GPU architecture needed for host-side programming
- [[L04-Rust-Breaking-the-Rules]] — Rust unsafe needed for RustaCUDA device buffer management

## Concepts Covered

- [[cuda-host-code]]
- [[rustacuda]]
- [[cuda-context]]
- [[cuda-module]]
- [[cuda-stream]]
- [[cuda-device-buffers]]
- [[cuda-kernel-launch]]
- [[cuda-blocks-and-grids]]
- [[cuda-grid-sizing]]
- [[device-copy-trait]]
- [[fp32-vs-fp64]]
- [[n-body-problem]]
