---
tags:
  - concept
  - ece459
  - rust
  - concurrency
lectures:
  - L03
prerequisites:
  - "[[ownership]]"
  - "[[borrowing-and-references]]"
  - "[[data-races]]"
  - "[[parallelism]]"
---

# Fearless Concurrency

Fearless concurrency is Rust's approach to making concurrency errors into compile-time errors rather than runtime bugs. Beyond preventing memory problems, Rust's ownership and borrowing rules also prevent data races and many common concurrency mistakes. The compiler does not make your concurrent program faster directly, but it helps indirectly: by catching bugs at compile time, you spend less time debugging and more time optimizing.

The practical benefit is confidence. If the compiler can verify that your concurrent code is correct, you do not have to spend as much time testing for race conditions. Bugs are prevented from being introduced in the first place, and if you are working on business-critical code, knowing no concurrency issue has been introduced makes it much easier to make changes. The key ideas of ownership and [[borrowing-and-references]] carry over naturally to concurrent contexts, preventing races without requiring you to learn an entirely new set of rules.

## Prerequisites
- [[ownership]] — Fearless concurrency is built on ownership rules preventing shared mutable state
- [[borrowing-and-references]] — Borrow rules carry over to concurrent contexts to prevent races
- [[data-races]] — Fearless concurrency eliminates data races at compile time
- [[parallelism]] — Understanding concurrency challenges motivates Rust's approach

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[rust-threads]]
- [[send-trait]]
- [[sync-trait]]
- [[mutex]]
- [[message-passing-channels]]
