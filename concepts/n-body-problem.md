---
tags:
  - concept
  - ece459
  - gpu
  - L21
  - L22
prerequisites:
  - "[[cuda-kernel]]"
  - "[[cuda-blocks-and-grids]]"
  - "[[data-parallelism]]"
---

# N-Body Problem

The N-body problem is used throughout the GPU lectures as a running example. It involves computing gravitational forces between all pairs of bodies -- an O(n^2) computation that is a good candidate for GPU parallelism.

The CUDA kernel uses `__device__` function `body_body_interaction` to compute pairwise forces, and a `__global__` function `calculate_forces` as the entry point. CUDA's `float4` and `float3` vector types package related values without custom structures.

Performance results on ecetesla1 with 100,000 points demonstrate the importance of proper [[cuda-grid-sizing]]:
- Sequential CPU: 40.3s
- Parallel CPU (Rayon): 5.3s
- CUDA (naive, 1 thread per block): 9.5s
- CUDA (optimized, 256 threads per block): 1.65s

The naive CUDA version was slower than the parallel CPU version because it did not properly utilize the GPU hardware. Correct block/grid sizing was essential.

## Prerequisites
- [[cuda-kernel]] — The N-body simulation is implemented as a CUDA kernel
- [[cuda-blocks-and-grids]] — Performance depends critically on proper block and grid sizing
- [[data-parallelism]] — The N-body problem is a data-parallel workload where each body is a work-item

## Lectures

- [[L21-GPU-Programming]]
- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-kernel]]
- [[cuda-blocks-and-grids]]
- [[cuda-grid-sizing]]
- [[cuda-host-code]]
