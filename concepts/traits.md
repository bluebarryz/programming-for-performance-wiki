---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites: []
---

# Traits

Traits in Rust are similar to interfaces in other languages. A trait defines a set of function signatures that a type must implement. You define a trait with `pub trait Name { ... }` and implement it with `impl Name for Type { ... }`. Traits can only be defined on your own types, not on external types from other crates, to avoid breaking other people's code.

Traits have several useful properties: they can have default implementations, they can be used as return types or method parameters (acting like generics), and they can be combined with `+` when you need a parameter to satisfy multiple traits. Three traits are particularly important for concurrency in this course: [[iterator-trait]], [[send-trait]], and [[sync-trait]].

## Prerequisites
None — foundational Rust concept.

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[iterator-trait]]
- [[send-trait]]
- [[sync-trait]]
