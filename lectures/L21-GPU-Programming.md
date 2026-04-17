---
tags:
  - lecture
  - ece459
  - gpu
  - cuda
  - heterogeneous-programming
lecture: L21
title: GPU Programming (CUDA)
prerequisite_lectures:
  - "[[L17-Mostly-Data-Parallelism]]"
  - "[[L04-Rust-Breaking-the-Rules]]"
---

# L21 - GPU Programming (CUDA)

This lecture introduces heterogeneous programming using GPUs, specifically NVIDIA's CUDA architecture. It covers the SIMT (Single Instruction Multiple Thread) programming model, where you write a kernel that runs on the GPU in a massively parallel fashion. The lecture explains the memory hierarchy (private, local/shared, global, constant, texture memory), how to write kernels using `__global__` and `__device__` functions, how work-items are organized into blocks on an ND-Range grid, and the role of warps. It also discusses branching costs on GPUs (all branches in a warp are executed), loop unrolling, and atomic functions for avoiding race conditions.

## Prerequisite Lectures
- [[L17-Mostly-Data-Parallelism]] — Data parallelism and SIMD concepts needed to understand GPU's massively parallel model
- [[L04-Rust-Breaking-the-Rules]] — Rust unsafe needed for RustaCUDA FFI and device memory management

## Concepts Covered

- [[heterogeneous-programming]]
- [[simt]]
- [[cuda]]
- [[opencl]]
- [[gpu-programming-model]]
- [[cuda-kernel]]
- [[data-parallelism]]
- [[work-items-and-index-space]]
- [[cuda-blocks-and-grids]]
- [[gpu-warps]]
- [[gpu-memory-hierarchy]]
- [[gpu-shared-memory]]
- [[nvcc-compiler]]
- [[ptx]]
- [[cuda-device-and-global-functions]]
- [[gpu-branching]]
- [[gpu-loop-unrolling]]
- [[cuda-atomic-functions]]
- [[n-body-problem]]
