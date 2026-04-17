---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[borrowing-and-references]]"
  - "[[ownership]]"
  - "[[rust-threads]]"
---

# Closures and Capturing

A closure in Rust is an anonymous function that can capture variables from its enclosing environment. Closures are the primary mechanism for passing work to threads via `thread::spawn`. The body of a closure can reference variables declared outside of it, and the compiler will analyze the request and figure out what needs to happen to make it work -- borrowing the value, copying it, or moving ownership.

When passing data to a thread, capturing by reference often does not work because the compiler cannot be sure the thread will not outlive the borrowed data. The fix is to use the [[move-keyword]] before the closure to transfer ownership into the thread. You can also clone-and-move if the original data is still needed. Closures are also used heavily in iterator chains and callback-based APIs like [[libcurl-easy-and-multi]].

## Prerequisites
- [[borrowing-and-references]] — Closures capture variables by borrowing or moving
- [[ownership]] — The compiler determines whether a closure borrows, copies, or takes ownership
- [[rust-threads]] — Closures are the primary way to pass work to threads

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[rust-threads]]
- [[move-keyword]]
- [[callbacks]]
