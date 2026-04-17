---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[borrowing-and-references]]"
  - "[[immutability-by-default]]"
  - "[[data-races]]"
---

# Mutable References

Mutable references in Rust allow borrowed data to be modified, declared with `&mut`. They come with strict restrictions enforced by the [[borrow-checker]]: while a mutable reference exists, the owner cannot change the data directly, there can be only one mutable reference at a time, and no immutable references can coexist with a mutable one. These rules prevent data races at compile time.

The restriction to a single mutable reference means there are never concurrent writes to the same data through references. As long as there are no mutable references, any number of immutable references can exist simultaneously, because reads do not interfere with each other. There is also a performance benefit: the compiler can cache values (including in CPU registers) without worrying they will become stale, since it knows no other reference can modify the data.

## Prerequisites
- [[borrowing-and-references]] — Mutable references extend immutable borrowing with write access
- [[immutability-by-default]] — Mutable references are the exception to Rust's default immutability
- [[data-races]] — The restriction to one mutable reference exists to prevent data races

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[borrowing-and-references]]
- [[borrow-checker]]
- [[fearless-concurrency]]
