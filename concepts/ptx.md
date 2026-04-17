---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[nvcc-compiler]]"
  - "[[cuda-kernel]]"
---

# PTX (Parallel Thread eXecution)

PTX is the intermediate representation that CUDA kernels are compiled into by the [[nvcc-compiler]]. It resembles assembly language. While it is possible to write PTX directly (as with any assembly language), the course lets the compiler handle it.

The compiled PTX is loaded at runtime as a [[cuda-module]] and can be included in Rust host code using `include_str!`. Using the `nvcc` compiler to produce PTX ensures the kernel will run on whatever hardware is available.

## Prerequisites
- [[nvcc-compiler]] — PTX is the output of the nvcc compilation step
- [[cuda-kernel]] — PTX is the compiled form of a CUDA kernel

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[nvcc-compiler]]
- [[cuda-kernel]]
- [[cuda-module]]
