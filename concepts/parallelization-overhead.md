---
tags:
  - concept
  - ece459
  - parallelism
lectures:
  - "09"
prerequisites:
  - "[[amdahls-law]]"
  - "[[concurrency-vs-parallelism]]"
---

# Parallelization Overhead

Parallelization overhead refers to the costs incurred by running code in parallel that do not exist in a sequential version. The most obvious source is thread creation and destruction: if tasks are short-lived and numerous, the time spent spawning and joining threads can become a significant fraction of total runtime. This is why [[thread-pools]] exist -- workers are created once and reused, amortizing the creation cost.

Amdahl's Law assumes that overheads do not matter and that the program behaves the same on 1 processor as on N, but in practice synchronization costs (lock contention, cache coherency traffic, memory barrier instructions) reduce the effective speedup below the theoretical maximum. The cost of synchronization between threads is an additional drag on performance that the basic formula does not account for.

Deciding how many threads to create depends on the workload. For computationally intensive tasks, fewer threads than the number of virtual CPUs may be optimal to avoid contention. For I/O-bound tasks, more threads can be useful since most will be waiting rather than computing. Amdahl's Law can help estimate the maximum useful number of threads, but experimentation is ultimately necessary to find the best configuration for a given workload and hardware.

## Prerequisites

- [[amdahls-law]] — Overhead reduces effective speedup below the theoretical Amdahl's Law prediction
- [[concurrency-vs-parallelism]] — Understanding parallelism is needed to reason about its overhead costs

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]

## Related Concepts
- [[amdahls-law]]
- [[thread-pools]]
- [[locking-and-synchronization]]
- [[memory-allocators]]
