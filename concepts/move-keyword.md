---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[closures-and-capturing]]"
  - "[[move-semantics]]"
  - "[[rust-threads]]"
---

# Move Keyword

The `move` keyword in Rust is placed before a closure to force it to take ownership of the variables it captures, rather than borrowing them. This is essential when spawning threads, because the compiler cannot guarantee that the thread will not outlive the data it references. Using `move` before the closure in `thread::spawn(move || { ... })` transfers ownership of the captured variables into the thread.

Without `move`, the compiler reports an error (E0373) saying the borrowed value might not live long enough. The error message itself suggests the fix: add `move`. If you need the original data to remain available after the thread is spawned, you can clone it first and move the clone into the thread. An alternative temptation is to make the data `'static`, but the course warns against this -- it often just moves the problem elsewhere and can lead to memory that is kept around forever unnecessarily.

## Prerequisites
- [[closures-and-capturing]] — The move keyword modifies how closures capture variables
- [[move-semantics]] — The move keyword forces ownership transfer into the closure
- [[rust-threads]] — move is essential when spawning threads to ensure data outlives the thread

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[closures-and-capturing]]
- [[rust-threads]]
- [[static-lifetime]]
