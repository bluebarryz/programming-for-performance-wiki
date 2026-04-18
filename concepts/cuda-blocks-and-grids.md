---
tags:
  - concept
  - ece459
  - gpu
  - L21
  - L22
prerequisites:
  - "[[work-items-and-index-space]]"
  - "[[cuda-kernel]]"
---

# CUDA Blocks and Grids

CUDA organizes parallel work into a two-level hierarchy: a grid of blocks, where each [[cuda-block]] contains multiple threads. Blocks can share memory locally but must execute independently, allowing the GPU to schedule them in any order.

Key sizing guidance: the number of threads per block should be a multiple of 32 (the [[gpu-warps|warp]] size), with a maximum of 512 or 1024 depending on the device. Common choices are 128 or 256 threads per block. The grid size is then the total number of work-items divided by the threads per block.

In the N-body example, the naive approach of one work-item per block (grid size = NUM_POINTS, block size = 1) ran in 9.5 seconds. After switching to 256 threads per block with proper indexing (`threadIdx.x + blockIdx.x * blockDim.x`), the same computation ran in 1.65 seconds -- a dramatic speedup from properly utilizing the hardware.

## Prerequisites
- [[work-items-and-index-space]] — Blocks and grids organize work-items into a hierarchy
- [[cuda-kernel]] — Blocks and grids define how a kernel's threads are structured

## Lectures

- [[L21-GPU-Programming]]
- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[gpu-warps]]
- [[cuda-block]]
- [[work-items-and-index-space]]
- [[cuda-kernel-launch]]
- [[cuda-grid-sizing]]
