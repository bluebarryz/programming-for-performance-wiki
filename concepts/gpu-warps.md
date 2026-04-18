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

tldr; warp = a group of 32 threads that execute simultaneously.

A warp is NVIDIA's term for a unit of execution on the GPU. It is a group of 32 threads that execute in lockstep. When choosing block sizes, you want to use a multiple of the warp size (32) to make best use of the hardware.

The warp model has important consequences for [[gpu-branching]]: all threads in a warp execute all branches taken by any thread in that warp, keeping only the valid results. This means divergent control flow within a warp is especially costly.

Similarly, if threads in a warp have loops of different lengths, the warp waits for the maximum number of iterations across all threads.

Q: *Do all threads in the same warp have to come from the same block?*
A: Yes. Warps are formed by partitioning a [[block]]'s threads into consecutive groups of 32 (threads 0–31 → warp 0, 32–63 → warp 1, etc.). <u>A warp never spans block boundaries</u>.
- If a block's thread count isn't a multiple of 32, the last warp has idle lanes. E.g. 100 threads/block → 4 warps, with 28 active + 4 idle in the last one.
- That's why the L22 guidance says threads per block should be a multiple of 32 — otherwise every block pays a partial-warp tax.
- Blocks are the unit that shares `__shared__` memory and synchronizes via `__syncthreads()`, so it wouldn't make sense for a warp to straddle two blocks that can't coordinate.


## Why Block Size Matters: N-Body in L22

[[L22-GPU-Programming-Continued]] demonstrates the cost of ignoring warp size using the [[n-body-problem]] on ecetesla1 with 100,000 points:

| Version | Config | Time |
| --- | --- | --- |
| Naive CUDA | 1 thread per block (`NUM_POINTS` blocks × 1 thread) | 9.5s |
| Tuned CUDA | 256 threads per block (`NUM_POINTS/256 + 1` blocks × 256 threads) | 1.65s |

**Before:** launching with one thread per block meant each warp had 1 active lane and 31 idle lanes — the hardware still executed the warp as a 32-wide unit, so 31/32 of the GPU's execution slots were wasted. The naive CUDA version (9.5s) was actually **slower than the parallel CPU** version (5.3s with Rayon).

**After:** packing 256 threads per block gives each warp a full 32 active lanes, and each block contains 8 fully-utilized warps. This delivered a **~5.7× speedup** (9.5s → 1.65s) purely from matching the launch config to the warp hardware.

Two code changes were required:
1. Launch config: `<<<(NUM_POINTS/256) + 1, 256, 0, stream>>>` (the `+1` handles non-divisibility so trailing accelerations aren't skipped).
2. Kernel index: change from `blockIdx.x` to `threadIdx.x + blockIdx.x * blockDim.x`, since 256 work-items now share a block.

Takeaway: threads per block should always be a multiple of 32, capped at 512–1024 depending on hardware; 128 or 256 are good starting points.

## Prerequisites
- [[simt]] — Warps are the hardware unit that executes SIMT instructions in lockstep
- [[cuda-blocks-and-grids]] — Warp size determines optimal block sizing

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda-blocks-and-grids]]
- [[gpu-branching]]
- [[simt]]
