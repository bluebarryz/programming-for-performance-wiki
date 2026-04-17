---
tags:
  - concept
  - ece459
  - gpu
prerequisites:
  - "[[cuda-blocks-and-grids]]"
  - "[[gpu-warps]]"
  - "[[cuda-kernel-launch]]"
---

# CUDA Grid Sizing

CUDA grid sizing is about choosing the right number of blocks and threads per block to fully utilize GPU hardware. The naive approach of assigning one work-item per block wastes the GPU's parallel capacity, since each block uses only one thread while the hardware supports many threads per block.

The key guidance from NVIDIA documentation is that threads per block should be a multiple of 32 (the warp size), with a maximum of 512 or 1024 depending on the device. Good starting values are 128 or 256 threads per block. The grid size (number of blocks) is then calculated as the total number of work-items divided by the threads per block, with a +1 to handle cases where the division is not even.

In the N-body example, the initial launch with grid size = NUM_POINTS and block size = 1 ran in 9.5 seconds -- worse than the parallel CPU version. After adjusting to 256 threads per block with `(NUM_POINTS/256) + 1` blocks, and updating the kernel to compute `idx = threadIdx.x + blockIdx.x * blockDim.x`, the same computation dropped to 1.65 seconds. This also required adding a bounds check (`if idx >= num_points { return; }`) to handle the extra threads in the last block.

## Prerequisites
- [[cuda-blocks-and-grids]] — Grid sizing determines how many blocks and threads per block to use
- [[gpu-warps]] — Optimal thread counts must be multiples of the warp size (32)
- [[cuda-kernel-launch]] — Grid and block sizes are specified at launch time

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-blocks-and-grids]]
- [[cuda-kernel-launch]]
- [[work-items-and-index-space]]
- [[gpu-warps]]
