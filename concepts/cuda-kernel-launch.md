---
tags:
  - concept
  - ece459
  - gpu
prerequisites:
  - "[[cuda-host-code]]"
  - "[[cuda-blocks-and-grids]]"
  - "[[cuda-stream]]"
  - "[[cuda-device-buffers]]"
---

# CUDA Kernel Launch

Launching a CUDA kernel involves several steps from the host (CPU) side: initializing the CUDA runtime, obtaining a device, creating a context and stream, loading the compiled kernel module, allocating device buffers, copying input data, launching the kernel, synchronizing, and copying results back to host memory.

In the course, the Rustacuda library is used to interface with CUDA from Rust. The launch happens inside an `unsafe` block because GPU interfacing code cannot respect Rust's safety guarantees. The `launch!` macro specifies the kernel function, grid size, block size, dynamic shared memory size, stream, and kernel arguments. Each buffer is passed via `as_device_ptr()`, while scalar types are passed directly. Kernel launches are asynchronous -- the host must call `stream.synchronize()` to wait for completion before reading results.

The host code follows a specific sequence: initialize with `CudaFlags::empty()`, get a device, create and push a context, load the PTX module from a compiled kernel string, create a stream, allocate `DeviceBuffer` objects for input and output data, launch the kernel, synchronize, and copy results back with `copy_to()`. The choice of grid size and block size in the launch call has significant performance implications.

## Prerequisites
- [[cuda-host-code]] — The kernel launch is the central step in the host code sequence
- [[cuda-blocks-and-grids]] — Launch parameters include grid and block dimensions
- [[cuda-stream]] — Kernels are launched on a stream
- [[cuda-device-buffers]] — Input/output buffers must be allocated before launch

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-blocks-and-grids]]
- [[cuda-grid-sizing]]
- [[device-copy-trait]]
- [[work-items-and-index-space]]
