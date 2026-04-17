---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[ownership]]"
  - "[[rust-memory-management]]"
---

# Box Smart Pointer

`Box<T>` is Rust's simplest smart pointer for heap allocation. It puts data on the heap rather than the stack, which is useful when the size is not known at compile time (e.g., user input) or when you want to transfer ownership of large data without copying (for performance). You create a box with `Box::new(...)`, and it is heap-allocated with all the usual ownership rules -- it gets dropped when the owner goes out of scope.

`Box<T>` is the starting point before the more complex reference-counted types. Unlike [[rc-reference-counting]] and [[arc-atomic-reference-counting]], a `Box` has a single owner and cannot be shared. It is the right choice when you simply need heap allocation without shared ownership.

## Prerequisites
- [[ownership]] — Box follows ownership rules with single-owner heap allocation
- [[rust-memory-management]] — Box is a mechanism for explicit heap allocation

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[rc-reference-counting]]
- [[arc-atomic-reference-counting]]
