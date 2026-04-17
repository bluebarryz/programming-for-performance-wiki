---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[gpu-branching]]"
  - "[[gpu-warps]]"
---

# GPU Loop Unrolling

On GPUs, executing a loop causes the workgroup to wait for the maximum number of iterations of that loop across all work-items. The [[nvcc-compiler]] will try to unroll loops when they have a known, constant number of iterations, replacing the loop with repeated straight-line code.

For example, a loop `for (int i = 0; i < 12; ++i)` can be fully unrolled by the compiler. This avoids the overhead of loop control and the warp synchronization cost of variable-length loops. This is especially important given the cost of [[gpu-branching]] in a [[simt]] architecture.

## Prerequisites
- [[gpu-branching]] — Loop unrolling mitigates the high cost of GPU branching
- [[gpu-warps]] — Warps wait for the maximum loop iteration count, motivating unrolling

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[gpu-branching]]
- [[gpu-warps]]
- [[nvcc-compiler]]
