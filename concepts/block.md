---
tags:
  - concept
  - ece459
  - gpu
  - L21
  - L22
prerequisites:
  - "[[cuda-kernel]]"
  - "[[gpu-programming-model]]"
---

# CUDA Block

tldr; block = a group of threads that run on the same SM, share memory, and can synchronize with each other.

A **block** is the middle level of CUDA's execution hierarchy: a [[cuda-kernel]] launch creates a grid of blocks, and each block contains many threads. Blocks are the unit the GPU scheduler hands to a streaming multiprocessor (SM); all threads in one block execute on that same SM for the block's lifetime.

## What threads in a block share

Grouping threads into blocks isn't just bookkeeping — it defines what they can do together:
- **[[gpu-shared-memory|Shared memory]]** (`__shared__`) is scoped to a single block. Threads from different blocks cannot see each other's shared memory.
- **Synchronization** via `__syncthreads()` is a block-wide barrier. There is no cross-block barrier inside a kernel.
- **[[gpu-warps|Warps]]** are formed by partitioning a block's threads into consecutive groups of 32 — a warp never spans two blocks. This is why `__syncthreads()` works at block scope: all warps that need to coordinate are guaranteed to live on the same SM.

Conversely, blocks execute **independently** of each other. The runtime is free to schedule them in any order (or simultaneously across SMs), which is what lets a single kernel scale across any number of SMs without code changes.

## Identifying a thread

Inside a kernel, each thread locates itself via built-in variables:
- `threadIdx.x/y/z` — thread's index within its block
- `blockIdx.x/y/z` — block's index within the grid
- `blockDim.x/y/z` — number of threads per block
- `gridDim.x/y/z` — number of blocks per grid

The standard 1-D global index formula is `threadIdx.x + blockIdx.x * blockDim.x`, which is why the L22 N-body fix had to change from `blockIdx.x` alone (one thread per block) to the full formula (256 threads per block).

## Sizing a block

Block size is set at launch: `<<<gridDim, blockDim>>>`. Rules of thumb from [[L22-GPU-Programming-Continued]]:
- Always a multiple of 32 — otherwise the last warp has idle lanes (see [[gpu-warps]]).
- Maximum 512 or 1024 threads per block depending on hardware.
- 128 or 256 are good defaults.

The [[n-body-problem]] in L22 is the canonical cautionary tale: launching with 1 thread per block ran at 9.5s; switching to 256 threads per block dropped to 1.65s — a ~5.7× speedup purely from picking a block size that fills warps.

## Prerequisites
- [[cuda-kernel]] — Blocks are how a kernel's threads are organized
- [[gpu-programming-model]] — Blocks are the scheduling unit on the GPU

## Lectures

- [[L21-GPU-Programming]]
- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-blocks-and-grids]]
- [[gpu-warps]]
- [[gpu-shared-memory]]
- [[cuda-grid-sizing]]
- [[cuda-kernel-launch]]
- [[n-body-problem]]
