---
tags:
  - concept
  - ece459
  - concurrency
lectures:
  - "09"
prerequisites:
  - "[[rust-threads]]"
  - "[[concurrency-vs-parallelism]]"
  - "[[parallelization-overhead]]"
---

# Thread Pools

A thread pool is a collection of pre-created worker threads that accept and execute units of work. Instead of spawning a new thread for each task and destroying it upon completion, the workers are created once and reused. This eliminates the overhead of frequent thread creation and destruction, which can be significant when tasks are numerous and short-lived.

The application submits work items to the pool, which distributes them to available workers. The number of workers scales based on the available hardware, decoupling the application from the specifics of the underlying system. The optimal number of threads depends on the workload: computationally intensive tasks benefit from having fewer threads than virtual CPUs (to avoid contention), while I/O-bound tasks can use more threads since most will be blocked waiting.

Thread pools are provided by most modern languages and frameworks: Java's `ThreadPoolExecutor`, C#'s `ThreadPool`, GLib's `GThreadPool`, and the Rust `threadpool` crate. In the Rust example from the lecture, a pool of 8 workers is created, and 4 consumer jobs are submitted. Each job loops, pulling items from a shared `Arc<Mutex<VecDeque>>` until it encounters a termination signal. The pool's `join()` method waits for all workers to finish, simplifying the otherwise tedious process of individually joining spawned threads.

## Prerequisites

- [[rust-threads]] — Thread pools manage pre-created threads from L03
- [[concurrency-vs-parallelism]] — Thread pools are a practical mechanism for parallel execution
- [[parallelization-overhead]] — Thread pools exist to amortize thread creation/destruction overhead

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]

## Related Concepts
- [[concurrency-vs-parallelism]]
- [[parallelization-overhead]]
- [[locking-and-synchronization]]
- [[memory-allocators]]
