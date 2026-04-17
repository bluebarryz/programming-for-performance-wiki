---
tags:
  - concept
  - ece459
  - concurrency
lectures:
  - "09"
  - "10"
prerequisites:
  - "[[amdahls-law]]"
  - "[[mutex]]"
  - "[[deadlocks]]"
  - "[[concurrency-vs-parallelism]]"
---

# Locking and Synchronization

Locking and synchronization are fundamental barriers to parallelization. The more locks and locking a program requires, the less scalable it becomes. A lock is effectively a shared resource: the more threads contending for it, the more time is spent waiting and coordinating rather than doing useful work. This applies equally to other synchronization constructs like semaphores and condition variables -- any time a thread is forced to wait limits the ability to parallelize.

In the context of [[amdahls-law]], synchronization points contribute to the serial fraction of the program. Even if the core computation is highly parallel, frequent lock acquisition serializes execution. The cost of synchronization between threads is not accounted for in the basic Amdahl's Law formula, meaning real-world speedups are often worse than the theoretical prediction.

A practical example from L10 is having every thread contend for a single `Arc<Mutex<Vector>>`. This can be made more efficient by switching to a message-passing model where one thread owns the data and others communicate via channels. While channels have overhead, they eliminate lock contention entirely. The broader lesson is that minimizing synchronization points -- through better data ownership, lock-free algorithms, or architectural changes -- is critical for achieving good parallel performance.

## Prerequisites

- [[amdahls-law]] — Synchronization points contribute to the serial fraction that Amdahl's Law bounds
- [[mutex]] — Mutexes from L03/L04 are the primary locking mechanism in Rust
- [[deadlocks]] — Deadlocks from L01 are a key risk of locking
- [[concurrency-vs-parallelism]] — Locking limits the degree to which concurrent code can run in parallel

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]
- [[L10-Software-Architecture]]

## Related Concepts
- [[concurrency-vs-parallelism]]
- [[amdahls-law]]
- [[thread-pools]]
- [[async-io-and-waiting]]
