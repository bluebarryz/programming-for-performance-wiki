---
tags:
  - concept
  - ECE459
  - L02
  - rust
prerequisites:
  - "[[ownership]]"
  - "[[move-semantics]]"
---

# Copy and Drop Traits

Ownership and move semantics are overkill for simple types. Types that implement the `Copy` trait (integers, booleans, floats, and other stack-only types with known size at compile time) follow copy semantics instead of move semantics. Assigning `let y = x;` for a `Copy` type creates two independent values -- both `x` and `y` remain valid.

The `Copy` trait is mutually exclusive with the `Drop` trait. A type cannot implement both. `Drop` is for types that need custom cleanup when they go out of scope (like freeing heap memory). Types with a heap component (like `String`, `Vec`) implement `Drop` and use move semantics.

If you need a copy of a non-`Copy` type, call `.clone()` explicitly.

## Prerequisites
- [[ownership]] — Copy and Drop define how types interact with ownership rules
- [[move-semantics]] — Copy trait provides an alternative to move semantics for simple types

## Lectures

- [[L02-Rust-Basics]]

## Related Concepts

- [[ownership]]
- [[move-semantics]]
- [[traits]]
