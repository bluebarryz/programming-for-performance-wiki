---
tags:
  - concept
  - ece459
  - rust
  - concurrency
lectures:
  - L03
  - L04
prerequisites:
  - "[[data-races]]"
  - "[[rust-threads]]"
  - "[[raii]]"
---

# Mutex

In Rust, a `Mutex<T>` wraps a value of type `T` and enforces mutual exclusion for access. You create one with `Mutex::new(value)`, and the mutex goes with the value it protects, making the association between lock and data explicit. To access the data, you call `lock()` which returns a `MutexGuard` -- the lock is automatically released when the guard goes out of scope.

A common pattern is to use manual scoping with `{ }` braces so the lock is released as soon as you are done with it, not at the end of the function. To share a mutex across threads, you cannot simply move it (that would violate single ownership), so you need [[arc-atomic-reference-counting]] to give multiple threads shared ownership: `Arc::new(Mutex::new(value))`. Rust's mutex does not prevent deadlocks -- nothing stops thread 1 from acquiring mutex A then B while thread 2 acquires B then A.

## Prerequisites
- [[data-races]] — Mutexes exist to prevent data races on shared state
- [[rust-threads]] — Mutexes are used to share state safely between threads
- [[raii]] — The MutexGuard uses RAII to automatically release the lock

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[arc-atomic-reference-counting]]
- [[fearless-concurrency]]
- [[sync-trait]]
