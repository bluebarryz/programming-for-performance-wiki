---
tags:
  - concept
  - ece459
  - concurrency
lectures:
  - "09"
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[concurrency-vs-parallelism]]"
---

# Memory Allocators

Memory allocators are a potential scalability bottleneck in parallel programs. Unless all memory is statically allocated in advance (as in some embedded systems), dynamic memory allocation is required. The default memory allocator is often centralized and may support only one thread allocating or deallocating at a time, effectively serializing all memory operations across threads.

This centralized design means the allocator does not scale well with increasing thread counts. When many threads are frequently allocating and freeing memory, the allocator becomes a contention point that limits parallelism -- similar to how a single lock on shared data serializes access.

There are, however, techniques for parallel-friendly dynamic memory allocation. Thread-local allocation pools, per-thread arenas (as used by allocators like jemalloc and mimalloc), and lock-free allocation strategies allow multiple threads to allocate memory concurrently without contending on a single global lock. Choosing an appropriate allocator can meaningfully improve the performance of memory-intensive parallel programs.

## Prerequisites

- [[locking-and-synchronization]] — A centralized allocator is effectively a global lock that serializes memory operations
- [[concurrency-vs-parallelism]] — Allocator contention limits parallel scalability

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]

## Related Concepts
- [[locking-and-synchronization]]
- [[parallelization-overhead]]
- [[concurrency-vs-parallelism]]
