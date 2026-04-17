---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[data-parallelism]]"
---

# SIMT (Single Instruction Multiple Thread)

SIMT is the term vendors use to describe GPU-style vector programming. It is closely related to SIMD (Single Instruction Multiple Data) but operates at the thread level. In a SIMT architecture, a single instruction is broadcast to many threads, each operating on different data.

A key consequence of SIMT is that [[gpu-branching]] is expensive: unlike a CPU, there is neither branch prediction nor speculative execution. All threads in a [[gpu-warps|warp]] execute all branches, keeping only the valid results. This means conditional logic should be minimized in [[cuda-kernel|kernels]].

## Prerequisites
- [[data-parallelism]] — SIMT is the GPU execution model for data-parallel workloads

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda]]
- [[gpu-warps]]
- [[gpu-branching]]
- [[data-parallelism]]
