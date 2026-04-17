---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[ownership]]"
  - "[[move-semantics]]"
---

# Borrowing and References

Borrowing is Rust's mechanism for letting a function use data without taking ownership of it. Instead of transferring ownership (which would prevent the caller from using the value afterward), you pass a reference using the `&` operator. The reference operator appears in both the function definition and the call site, making it explicit whether ownership or a reference is being provided.

When a function borrows a value via a reference, ownership stays with the original variable. The reference goes out of scope at the end of the function where it was used, but the original data remains valid. By default, references are immutable -- you cannot modify borrowed data, even if the underlying variable is mutable. This is a deliberate design choice to prevent race conditions: if nobody can write through a reference, concurrent reads are always safe.

References cannot outlive the data they point to. If a function tries to return a reference to data created inside that function, the [[borrow-checker]] will reject it, preventing the dangling-pointer bugs common in C and C++.

## Prerequisites
- [[ownership]] — Borrowing is an alternative to transferring ownership
- [[move-semantics]] — References avoid the need to move values into functions

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[borrow-checker]]
- [[mutable-references]]
- [[lifetimes]]
- [[slices]]
