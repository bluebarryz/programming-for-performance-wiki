---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[data-parallelism]]"
---

# Heterogeneous Programming

Heterogeneous programming refers to writing software that targets multiple types of processing units, typically a CPU and a GPU. The general idea is to leverage vector programming via SIMT (Single Instruction Multiple Thread). Historical examples include the PlayStation 3's Cell architecture (a PowerPC core plus 8 SIMD coprocessors) and modern NVIDIA GPUs via [[cuda]].

The programming model is: write the massively parallel computation (the [[cuda-kernel]]) separately from the main code, transfer data to the GPU at runtime, execute the kernel, and transfer results back. This makes sense when the workload is large enough to amortize the significant setup and transfer overhead -- analogous to choosing to fly vs. drive based on distance.

## Prerequisites
- [[data-parallelism]] — Understanding data-parallel workloads explains why GPUs are useful for heterogeneous programming

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda]]
- [[opencl]]
- [[simt]]
- [[gpu-programming-model]]
