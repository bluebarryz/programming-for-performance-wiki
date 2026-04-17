---
tags:
  - concept
  - ECE459
  - L02
  - L03
  - rust
prerequisites:
  - "[[ownership]]"
---

# Move Semantics

Move semantics transfer ownership from one variable to another. When you assign a heap-allocated value like `let s2 = s1;`, ownership transfers from `s1` to `s2`, and `s1` is no longer valid. Using `s1` after the move is a compile-time error.

This is different from C++ pointer assignment, where `thing* p = (thing*) ptr;` creates two pointers to the same memory. In Rust, the old variable is invalidated to preserve the "one owner" rule.

Moves also occur when:
- Passing a variable as an argument to a function (ownership transfers to the function parameter).
- Returning a value from a function (ownership transfers to the caller).

For performance, Rust won't automatically create deep copies. If you need a copy, call `.clone()` explicitly -- but cloning can be expensive (arbitrary memory allocation and data copying).

C++ has move semantics too, but uses copy semantics by default. Rust uses move semantics by default for heap-allocated types.

The `move` keyword before a closure forces the closure to take ownership of captured variables rather than borrowing them, which is essential for [[rust-threads|thread spawning]].

## Prerequisites
- [[ownership]] — Move semantics transfer ownership between variables

## Lectures

- [[L02-Rust-Basics]]
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts

- [[ownership]]
- [[copy-and-drop-traits]]
- [[borrowing-and-references]]
- [[move-keyword]]
