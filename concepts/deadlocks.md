---
tags:
  - concept
  - ECE459
  - L01
  - L04
  - concurrency
prerequisites:
  - "[[parallelism]]"
---

# Deadlocks

A deadlock occurs when none of the threads or processes can make progress on the task because of a cycle in resource requests. To avoid a deadlock, the programmer needs to enforce an ordering on the locks, or use some other strategy.

In Rust, even though the mutex is automatically unlocked when the `MutexGuard` goes out of scope, deadlocks are still possible. Nothing prevents thread 1 from acquiring mutex A then B, and thread 2 from concurrently acquiring B then A. Rust cannot solve all concurrency problems -- it prevents data races but not deadlocks.

## Prerequisites
- [[parallelism]] — Deadlocks occur between concurrent threads/processes competing for resources

## Lectures

- [[L01-Programming-for-Performance]]
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts

- [[data-races]]
- [[parallelism]]
- [[mutex]]
- [[fearless-concurrency]]
