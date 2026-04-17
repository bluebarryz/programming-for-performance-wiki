---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[data-parallelism]]"
  - "[[cuda-kernel]]"
---

# Work-Items and Index Space

A work-item is the fundamental unit of work in GPU computing. Each work-item lives on an n-dimensional grid called the ND-Range (or index space). CUDA spawns a thread for each work-item, with a unique thread ID.

Work-items are grouped into [[cuda-blocks-and-grids|blocks]]. Blocks can share memory locally but must be able to execute independently, allowing the system to schedule them in any order. You can divide the ND-Range into smaller work-groups yourself or let the system do it.

Problems can be 1D (vector operations), 2D (image processing), or 3D (volume rendering). The limit of three dimensions likely stems from GPUs being designed for 3D rendering. For higher-dimensional problems, you can flatten dimensions into a linear array.

## Prerequisites
- [[data-parallelism]] — Each work-item processes a separate data element in parallel
- [[cuda-kernel]] — Work-items are the units of execution within a kernel

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda-blocks-and-grids]]
- [[data-parallelism]]
- [[gpu-warps]]
