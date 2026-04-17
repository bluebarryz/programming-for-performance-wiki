---
tags:
  - concept
  - ece459
  - rust
  - concurrency
lectures:
  - L03
prerequisites:
  - "[[traits]]"
  - "[[ownership]]"
  - "[[rust-threads]]"
---

# Send Trait

The `Send` trait indicates that ownership of a type can be safely transferred between threads. Almost all basic types in Rust implement `Send`, and any programmer-defined type composed entirely of `Send` types automatically has the trait. Some standard-library types deliberately do not implement `Send` to signal they are not intended for cross-thread use -- if the compiler tells you a type is not `Send`, it is a hint to use a different type.

The `Send` trait is required for values sent via [[message-passing-channels]] and for data moved into threads. [[rc-reference-counting]] notably does not implement `Send` because its internal counter is not managed in a thread-safe way. For thread-safe shared ownership, use [[arc-atomic-reference-counting]] instead.

## Prerequisites
- [[traits]] — Send is a trait; understanding the trait system is needed
- [[ownership]] — Send indicates ownership can be safely transferred across threads
- [[rust-threads]] — Send is required for data moved into threads

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[sync-trait]]
- [[traits]]
- [[arc-atomic-reference-counting]]
- [[rc-reference-counting]]
- [[message-passing-channels]]
