---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[cuda-kernel]]"
  - "[[gpu-shared-memory]]"
---

# CUDA Atomic Functions

Even on GPUs, race conditions are possible when multiple work-items concurrently access the same memory location. CUDA provides atomic functions to handle this safely. Atomic operations are available for standard primitive types (integers, floating point numbers) and include:

- Add, subtract, min, max, increment, decrement
- Compare-and-swap (CAS)
- Bitwise operations (and, or, xor)

The course shows an example of implementing `atomicAdd` for doubles using a compare-and-swap loop, since not all types have built-in atomic support. These are analogous to [[cuda]]-specific versions of the atomic operations seen in CPU concurrency.

## Prerequisites
- [[cuda-kernel]] — Atomic functions are used within kernels to avoid race conditions
- [[gpu-shared-memory]] — Atomic operations protect concurrent access to shared memory locations

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda-kernel]]
- [[gpu-shared-memory]]
