---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[cuda]]"
  - "[[gpu-programming-model]]"
---

# CUDA Kernel

A kernel is a function that runs on the GPU, executed by every CUDA thread in parallel. Kernels are written in a C++ variant and marked with `__global__` (callable from host) or `__device__` (callable from other device functions only).

In a kernel, the explicit loop from CPU code becomes implicit. Instead of iterating over indices, each thread determines its own index via built-in variables like `threadIdx.x`, `blockIdx.x`, and `blockDim.x`. For example, a CPU vector addition loop becomes:

```c
__global__ void vector_add(float* A, float* B, float* C) {
    int i = blockIdx.x;
    C[i] = A[i] + B[i];
}
```

Kernels lack the safety guarantees of Rust -- you can read off the end of arrays, have uninitialized variables, memory leaks, and race conditions. Always verify output correctness. The kernel is compiled by [[nvcc-compiler]] into [[ptx]] instructions.

## Prerequisites
- [[cuda]] — Kernels are written within the CUDA framework
- [[gpu-programming-model]] — Kernels are the parallel computation step in the GPU programming model

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda-device-and-global-functions]]
- [[cuda-blocks-and-grids]]
- [[nvcc-compiler]]
- [[ptx]]
- [[cuda-kernel-launch]]
