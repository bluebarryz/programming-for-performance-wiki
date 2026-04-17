---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[cuda]]"
  - "[[cuda-kernel]]"
---

# NVCC Compiler

`nvcc` is NVIDIA's kernel compiler for CUDA. It compiles kernel code (written in a C++ variant) into [[ptx]] instructions. The compiler has specific requirements for the underlying C/C++ compiler it relies on (e.g., the default `gcc` on specific ECE servers).

Usage example: `nvcc -ptx nbody.cu` compiles the kernel file into PTX format that can then be loaded at runtime. When changing machines (e.g., uploading from laptop to server), you should recompile to target the available hardware. The `nvcc` compiler will also try to [[gpu-loop-unrolling|unroll loops]] with known iteration counts.

## Prerequisites
- [[cuda]] — nvcc is the compiler for CUDA kernel code
- [[cuda-kernel]] — nvcc compiles kernel source into PTX

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda]]
- [[ptx]]
- [[cuda-kernel]]
