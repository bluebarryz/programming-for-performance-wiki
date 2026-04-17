---
tags:
  - concept
  - ece459
  - gpu
  - L22
prerequisites:
  - "[[gpu-programming-model]]"
  - "[[cuda-kernel]]"
  - "[[ptx]]"
---

# CUDA Host Code

Host code is the CPU-side program that sets up and launches GPU kernels. In the course, host code is written in Rust using the [[rustacuda]] library, avoiding the need to write the entire program in C/C++.

The host code follows a standard sequence:
1. Initialize the CUDA runtime (`CudaFlags::empty()`)
2. Get a [[cuda-context|device]] (`Device::get_device(0)`)
3. Create and push a [[cuda-context|context]]
4. Load the compiled [[ptx]] as a [[cuda-module|module]]
5. Create a [[cuda-stream|stream]] for issuing commands
6. Create [[cuda-device-buffers|device buffers]] for input/output data
7. Launch the kernel (in an `unsafe` block)
8. Synchronize (`stream.synchronize()`)
9. Copy results back to host memory

The kernel launch is asynchronous -- after launching, you can do other work before synchronizing. The `unsafe` block is required because GPU interfacing code cannot respect Rust's safety guarantees.

## Prerequisites
- [[gpu-programming-model]] — Host code implements the setup/transfer/launch/retrieve pattern
- [[cuda-kernel]] — Host code exists to launch and manage kernel execution
- [[ptx]] — The host loads compiled PTX modules at runtime

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[rustacuda]]
- [[cuda-kernel-launch]]
- [[cuda-device-buffers]]
- [[cuda-stream]]
- [[gpu-programming-model]]
