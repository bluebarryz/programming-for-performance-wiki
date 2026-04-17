---
tags:
  - concept
  - ece459
  - gpu
  - L21
  - L22
prerequisites:
  - "[[data-parallelism]]"
  - "[[heterogeneous-programming]]"
---

# CUDA

CUDA (Compute Unified Device Architecture) is NVIDIA's architecture and programming framework for general-purpose GPU computing. "C for CUDA" predates [[opencl]], and NVIDIA makes CUDA tools readily available. CUDA may be faster than OpenCL on NVIDIA hardware, and it supports most C++ features, which OpenCL does not.

Kernels are written in a C++ variant with additions like `__global__` and `__device__` function qualifiers. The [[nvcc-compiler]] compiles kernels into [[ptx]] (Parallel Thread eXecution) instructions. The course uses CUDA because it has found widespread industry acceptance; the principles transfer to OpenCL if cross-platform or AMD support is needed.

CUDA uses [[cuda-blocks-and-grids]] to organize parallel work, with threads grouped into blocks that share local memory and can execute independently.

## Prerequisites
- [[data-parallelism]] — CUDA is a framework for executing data-parallel workloads on GPUs
- [[heterogeneous-programming]] — CUDA is NVIDIA's specific implementation of heterogeneous programming

## Lectures

- [[L21-GPU-Programming]]
- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[opencl]]
- [[cuda-kernel]]
- [[nvcc-compiler]]
- [[ptx]]
- [[cuda-blocks-and-grids]]
- [[gpu-memory-hierarchy]]
