---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[simt]]"
  - "[[cuda-blocks-and-grids]]"
---

# GPU Warps

A warp is NVIDIA's term for a unit of execution on the GPU. It is a group of 32 threads that execute in lockstep. When choosing block sizes, you want to use a multiple of the warp size (32) to make best use of the hardware.

The warp model has important consequences for [[gpu-branching]]: all threads in a warp execute all branches taken by any thread in that warp, keeping only the valid results. This means divergent control flow within a warp is especially costly.

Similarly, if threads in a warp have loops of different lengths, the warp waits for the maximum number of iterations across all threads.

## Prerequisites
- [[simt]] — Warps are the hardware unit that executes SIMT instructions in lockstep
- [[cuda-blocks-and-grids]] — Warp size determines optimal block sizing

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda-blocks-and-grids]]
- [[gpu-branching]]
- [[simt]]
