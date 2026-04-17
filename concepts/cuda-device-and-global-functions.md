---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[cuda-kernel]]"
  - "[[gpu-programming-model]]"
---

# CUDA __device__ and __global__ Functions

CUDA uses function qualifiers to distinguish where functions run and who can call them:

- **`__global__`**: Marks a kernel function callable from the host (CPU). These are the entry points into GPU code. Global functions can call device functions but not other global functions.
- **`__device__`**: Marks a function callable only from other GPU functions (device or global). These are "private" helper functions that run on the GPU.

The `extern "C"` declaration is often placed before `__global__` functions to disable C++ name mangling, ensuring the host code can find the function by its declared name. More modern versions of `nvcc` may not require this.

## Prerequisites
- [[cuda-kernel]] — __device__ and __global__ are the function qualifiers used to write kernels
- [[gpu-programming-model]] — These qualifiers define the boundary between host and device code

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda-kernel]]
- [[cuda]]
- [[cuda-kernel-launch]]
