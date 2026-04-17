---
tags:
  - concept
  - ECE459
  - L02
  - L03
  - L04
  - rust
  - memory
prerequisites:
  - "[[rust-memory-management]]"
  - "[[rust-motivation]]"
---

# Ownership

The most important concept that distinguishes Rust from other programming languages. Ownership is Rust's strategy for memory management and safe concurrency, enforced at compile time.

**The three rules:**

1. Every value has a variable that is its owner.
2. There can be only one owner at a time.
3. When the owner goes out of scope, the value is dropped (deallocated).

These rules mean the compiler determines at compile time when memory can be cleaned up. The advantage over RAII is that the compiler enforces "one owner" -- in C++ you can write code that breaks this invariant and get segfaults.

**How ownership prevents bugs:**
- **Memory leak** -- cannot happen because memory is deallocated when its owner goes out of scope.
- **Double-free** -- cannot happen because there is only one owner; deallocation happens exactly once.
- **Use-after-free** -- cannot happen because a reference to moved/freed data is a compile-time error.
- **Uninitialized memory** -- caught by the compiler.

Ownership can be transferred via [[move-semantics]]. For simple types (integers, booleans, floats), [[copy-and-drop-traits|copy semantics]] apply instead. When you need shared access without transferring ownership, use [[borrowing-and-references]].

## Prerequisites
- [[rust-memory-management]] — Ownership is Rust's core mechanism for memory management
- [[rust-motivation]] — Ownership exists to prevent the memory bugs that motivate using Rust

## Lectures

- [[L02-Rust-Basics]]
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts

- [[move-semantics]]
- [[copy-and-drop-traits]]
- [[borrowing-and-references]]
- [[raii]]
- [[rust-memory-management]]
- [[rc-reference-counting]]
- [[arc-atomic-reference-counting]]
- [[lifetimes]]
