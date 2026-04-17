---
tags:
  - concept
  - ece459
  - gpu
  - rust
  - L22
prerequisites:
  - "[[cuda-host-code]]"
  - "[[cuda]]"
---

# RustaCUDA

RustaCUDA is a Rust library that interfaces with the GPU, allowing host code to be written in Rust even though kernels must be written in C/C++ CUDA. This limits the amount of `unsafe` code to just the kernel launch itself.

The library provides types like `DeviceBuffer` for GPU memory allocation, and requires types sent to the kernel to implement the [[device-copy-trait|DeviceCopy]] trait, which promises the type contains no pointers to host memory (since those would be invalid on the GPU).

RustaCUDA's `launch!` macro takes the kernel function, grid size, block size, shared memory size, stream, and kernel arguments. Kernel launches are asynchronous -- you must call `stream.synchronize()` to wait for completion.

## Prerequisites
- [[cuda-host-code]] — RustaCUDA is the Rust library for writing CUDA host code
- [[cuda]] — Understanding CUDA concepts is needed to use the RustaCUDA API

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-host-code]]
- [[cuda-kernel-launch]]
- [[device-copy-trait]]
- [[cuda-stream]]
