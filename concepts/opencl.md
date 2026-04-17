---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[data-parallelism]]"
  - "[[heterogeneous-programming]]"
---

# OpenCL

OpenCL is a cross-platform framework for heterogeneous computing. Unlike [[cuda]], which is NVIDIA-specific, OpenCL works across different vendors including AMD. The course previously taught OpenCL but switched to CUDA due to CUDA's wider industry adoption.

The programming principles are similar enough between CUDA and OpenCL that learning one toolchain makes it straightforward to pick up the other -- the main differences are in syntax. If you need cross-platform GPU support or have AMD hardware, OpenCL is the right choice.

## Prerequisites
- [[data-parallelism]] — OpenCL targets data-parallel workloads across different hardware vendors
- [[heterogeneous-programming]] — OpenCL is a cross-platform approach to heterogeneous programming

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[cuda]]
- [[heterogeneous-programming]]
