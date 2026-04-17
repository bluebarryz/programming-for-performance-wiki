---
tags:
  - concept
  - ece459
  - gpu
  - L21
  - L22
prerequisites:
  - "[[data-parallelism]]"
  - "[[heterogeneous-programming]]"
---

# GPU Programming Model

The GPU programming model for heterogeneous architectures follows a consistent pattern:

1. Write the massively parallel computation ([[cuda-kernel]]) separately from host code
2. At runtime, set up the data (input) and transfer it to the GPU
3. Wait while the GPU executes the kernel
4. Transfer the results back to host memory

There is significant setup cost for interacting with the GPU and transferring data, so the workload must be large enough to justify this overhead. GPUs have many cores running at slower speeds than CPUs (e.g., 1920 CUDA cores at 1.8 GHz vs. 4 CPU cores at 3.6 GHz), yielding a massive throughput advantage for suitable workloads -- primarily [[embarrassingly-parallel]] problems.

## Prerequisites
- [[data-parallelism]] — The GPU model assumes embarrassingly parallel, data-parallel workloads
- [[heterogeneous-programming]] — The GPU programming model is the concrete workflow for heterogeneous systems

## Lectures

- [[L21-GPU-Programming]]
- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-kernel]]
- [[heterogeneous-programming]]
- [[data-parallelism]]
- [[cuda-host-code]]
