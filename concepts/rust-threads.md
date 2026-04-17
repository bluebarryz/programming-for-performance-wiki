---
tags:
  - concept
  - ece459
  - rust
  - concurrency
lectures:
  - L03
prerequisites:
  - "[[fearless-concurrency]]"
  - "[[ownership]]"
  - "[[parallelism]]"
---

# Rust Threads

Rust uses threads for concurrency with a model resembling POSIX pthread create/join semantics. You spawn a thread with `thread::spawn`, passing it a closure (an anonymous function that captures its environment). The spawn call returns a `JoinHandle`, and calling `join()` on it waits for the thread to finish, similar to pthread_join.

There are three ways to get data from one thread to another: capturing variables in the closure, [[message-passing-channels]], and shared state (e.g., [[mutex]]). When capturing variables, the compiler may require you to use the [[move-keyword]] before the closure (`move || { ... }`) to transfer ownership of captured variables into the thread, since the compiler cannot guarantee the thread will not outlive the borrowed data.

## Prerequisites
- [[fearless-concurrency]] — Rust threads operate under the fearless concurrency model
- [[ownership]] — Thread spawning requires transferring ownership of captured data
- [[parallelism]] — Threads are the primary mechanism for parallel execution

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[fearless-concurrency]]
- [[closures-and-capturing]]
- [[move-keyword]]
- [[message-passing-channels]]
- [[send-trait]]
