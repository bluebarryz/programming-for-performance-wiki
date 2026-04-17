---
tags:
  - concept
  - ece459
  - gpu
prerequisites:
  - "[[rustacuda]]"
  - "[[cuda-device-buffers]]"
---

# DeviceCopy Trait

The `DeviceCopy` trait is a requirement of the Rustacuda library that any type sent to a CUDA kernel must implement. Implementing this trait promises that the type does not contain any pointers to host memory, since those pointers would be meaningless on the GPU device (which does not share host memory).

For example, a struct containing a pointer to a buffer cannot implement `DeviceCopy` because the pointer would be bogus on the GPU. In the N-body example, wrapper types `CudaFloat4` and `CudaFloat3` are created around CUDA's `float4` and `float3` vector types, with `unsafe impl DeviceCopy` to satisfy this requirement. The `Deref` trait is also implemented so the wrappers transparently behave like their inner types.

## Prerequisites
- [[rustacuda]] — DeviceCopy is a trait required by the RustaCUDA library
- [[cuda-device-buffers]] — Types sent to device buffers must implement DeviceCopy

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-kernel-launch]]
- [[cuda-blocks-and-grids]]
- [[copy-and-drop-traits]]
