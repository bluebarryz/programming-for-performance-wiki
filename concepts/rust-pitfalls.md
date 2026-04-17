---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[ownership]]"
  - "[[borrow-checker]]"
  - "[[result-and-error-handling]]"
  - "[[iterator-trait]]"
---

# Rust Pitfalls

The course identifies several common mistakes students and developers make in Rust, accumulated from years of observation:

- **Overuse of `'static` lifetime** to band-aid ownership issues instead of properly moving or cloning data.
- **Excessive `clone()` calls** to avoid borrow-checker complexity, which defeats the performance benefits of Rust's ownership model.
- **Array indexing instead of iterators** -- underestimating the overhead of bounds checking compared to using the [[iterator-trait]].
- **Unbuffered I/O** -- not using buffered readers/writers, leading to excessive system calls.
- **Expensive vector operations** like `resize()` that trigger reallocation and copying.
- **Blind `unwrap()` everywhere** with no error handling, risking panics in production (see [[result-and-error-handling]]).
- **Vibe coding** -- trusting LLM-generated code without verifying correctness or optimality.

## Prerequisites
- [[ownership]] — Many pitfalls involve misuse of ownership (excessive cloning, 'static abuse)
- [[borrow-checker]] — Understanding the borrow checker explains why students resort to anti-patterns
- [[result-and-error-handling]] — Blind unwrap() is a common pitfall covered here
- [[iterator-trait]] — Preferring iterators over array indexing is a key performance lesson

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[static-lifetime]]
- [[iterator-trait]]
- [[result-and-error-handling]]
- [[borrow-checker]]
