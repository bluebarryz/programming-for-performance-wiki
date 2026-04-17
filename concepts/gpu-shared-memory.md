---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[gpu-memory-hierarchy]]"
  - "[[cuda-blocks-and-grids]]"
---

# GPU Shared Memory

Shared memory (also called local memory in OpenCL terminology) is memory shared between work-items belonging to the same work-group/block. It is created by the compiler and includes values spilled from registers and small arrays declared inside kernels.

Using shared memory effectively can significantly improve performance over relying solely on [[gpu-memory-hierarchy|global memory]], since shared memory is much faster to access. However, each block has its own shared memory space, and blocks must be able to execute independently.

## Prerequisites
- [[gpu-memory-hierarchy]] — Shared memory is one level of the GPU memory hierarchy
- [[cuda-blocks-and-grids]] — Shared memory is scoped to a block

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[gpu-memory-hierarchy]]
- [[cuda-blocks-and-grids]]
