---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[borrowing-and-references]]"
  - "[[mutable-references]]"
  - "[[ownership]]"
---

# Borrow Checker

The borrow checker is a compile-time analysis in Rust that verifies all borrowing (use of references) in a program is safe. It enforces the rules that prevent data races and dangling references: you can have either one mutable reference or any number of immutable references to a value at a time, and references must not outlive the data they point to. If the borrow checker is not certain the code is safe, it rejects the program with a compile error.

The borrow checker errs on the side of caution -- its analysis is not perfect, and it will sometimes reject code that is actually safe. This can be frustrating, but the tradeoff is that programs that do compile are guaranteed free of data races and use-after-free bugs. There are escape hatches: you can use [[unsafe-rust]] to tell the compiler you guarantee safety yourself, or use constructs like [[rc-reference-counting]] and [[arc-atomic-reference-counting]] to work around ownership restrictions.

## Prerequisites
- [[borrowing-and-references]] — The borrow checker enforces the rules of borrowing
- [[mutable-references]] — The borrow checker validates mutable reference exclusivity
- [[ownership]] — The borrow checker verifies ownership invariants at compile time

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[borrowing-and-references]]
- [[mutable-references]]
- [[lifetimes]]
- [[non-lexical-lifetimes]]
- [[unsafe-rust]]
