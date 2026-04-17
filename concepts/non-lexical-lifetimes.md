---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[borrow-checker]]"
  - "[[borrowing-and-references]]"
---

# Non-Lexical Lifetimes

Non-lexical lifetimes (NLL) are an improvement to Rust's [[borrow-checker]] that allows the compiler to end a borrow as soon as the reference is no longer used, rather than at the end of the enclosing scope. Under the old rules, an immutable reference would be considered live until the end of its scope, which could prevent a mutable reference from being created even when there was no actual conflict.

With NLL, the compiler tracks the actual last use of each reference. For example, if you create an immutable borrow `y` of `x`, print `y`, and then create a mutable borrow `z` of `x`, the compiler sees that `y` is no longer used after the print and allows `z` to be created. The two references never exist at the same time, so the code is safe. This makes the borrow checker significantly less frustrating to work with in practice.

## Prerequisites
- [[borrow-checker]] — NLL is an improvement to how the borrow checker tracks reference liveness
- [[borrowing-and-references]] — NLL refines when borrows are considered active

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[borrow-checker]]
- [[borrowing-and-references]]
- [[mutable-references]]
- [[lifetimes]]
