---
tags:
  - concept
  - ece459
  - rust
  - concurrency
lectures:
  - L04
prerequisites:
  - "[[rc-reference-counting]]"
  - "[[rust-threads]]"
  - "[[send-trait]]"
---

# Arc (Atomic Reference Counting)

`Arc<T>` is the thread-safe version of [[rc-reference-counting]]. It uses atomic operations for its internal reference counter, making it safe to share across threads (it implements the [[send-trait]]). The typical pattern for sharing a [[mutex]] across threads is `Arc::new(Mutex::new(value))`, then cloning the `Arc` for each thread.

`Arc<T>` is slightly slower than `Rc<T>` due to the overhead of atomic operations on the counter, so you should only use it when you actually need cross-thread sharing. Like `Rc`, you cannot keep a reference to the value after the `Arc` goes out of scope -- the value is freed when the last `Arc` is dropped. The course shows a practical example of using `Arc` with a `Mutex<bool>` to set up a Ctrl-C signal handler that communicates with the main loop.

## Prerequisites
- [[rc-reference-counting]] — Arc is the thread-safe version of Rc
- [[rust-threads]] — Arc is needed to share data across threads
- [[send-trait]] — Arc implements Send, unlike Rc

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[rc-reference-counting]]
- [[mutex]]
- [[send-trait]]
- [[rust-threads]]
