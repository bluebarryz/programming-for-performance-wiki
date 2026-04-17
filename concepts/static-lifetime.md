---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[lifetimes]]"
  - "[[rust-threads]]"
---

# Static Lifetime

The `'static` lifetime grants a reference the ability to live for the entire duration of the program. String literals have the `'static` lifetime because they are baked into the binary. The thread-spawning interface requires `'static` bounds on captured data because threads can live arbitrarily long, and the compiler wants to guarantee the data will outlive the thread.

The course warns against using `'static` as a band-aid for ownership issues. When the compiler says a value passed to a thread needs to be `'static`, it often really means you should move the data, copy it, or use [[arc-atomic-reference-counting]]. Annotating a function parameter as `'static` just moves the problem to the call site. Memory kept around forever via `'static` is fundamentally similar to a memory leak, even if it could hypothetically be deallocated.

## Prerequisites
- [[lifetimes]] — 'static is a specific lifetime annotation meaning "lives for the entire program"
- [[rust-threads]] — Thread spawning requires 'static bounds on captured data

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[lifetimes]]
- [[arc-atomic-reference-counting]]
- [[rust-pitfalls]]
- [[move-keyword]]
