---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[cuda]]"
  - "[[cuda-kernel]]"
---

# GPU Memory Hierarchy

CUDA exposes several types of memory, each with different scope and performance characteristics:

- **Private memory**: available only to a single work-item
- **Local/shared memory**: shared between work-items in the same block; created by the compiler from spilled registers and small arrays declared inside kernels
- **Global memory**: shared between all work-items and the host; the main memory for data transfer
- **Constant memory**: resides on the GPU, cached, does not change
- **Texture memory**: also global and cached; provides a slight speedup over global memory for certain access patterns, leveraging the GPU's texture caching hardware
- **Host memory**: RAM in the computer, containing the application's data

Choosing the right memory type is an important design decision. Putting everything in global memory is simple but slow. Constant memory is tempting for unchanging data but has limited space. Explicit transfers between host and GPU memory are required in both directions.

## Prerequisites
- [[cuda]] — The memory hierarchy is specific to CUDA GPU architecture
- [[cuda-kernel]] — Understanding kernels is needed to know which memory types are accessible where

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[gpu-shared-memory]]
- [[cuda-device-buffers]]
- [[cuda]]
