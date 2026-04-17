---
tags:
  - concept
  - ECE459
  - L02
  - rust
prerequisites:
  - "[[data-races]]"
---

# Immutability by Default

Variables in Rust are, by default, immutable. Once a value has been assigned to a name, you cannot change it. This is a compile-time error:

```rust
let x = 42;
x = 17; // compile-time error!
```

This is good for performance because it helps the compiler reason about whether a data race may exist. No writes means no races. In C, a `const` declaration can be bypassed by casting pointers; Rust's immutability is enforced by the compiler (unless you use `unsafe`).

To make a variable mutable, explicitly declare it with `mut`: `let mut x = 42;`. The general advice is to minimize mutation -- use it only when it is clearly the best approach (e.g., mutating a large/complicated object in place is faster than making an altered copy).

Constants (`const`) are different from immutable variables: they are immortal, valid for their entire scope, never change, and don't exist at runtime (no address). Global variables defined with `static` are immutable by default but may point to mutable things (e.g., `Atomic*`, `Mutex`).

## Prerequisites
- [[data-races]] — Immutability prevents data races; understanding races motivates this design choice

## Lectures

- [[L02-Rust-Basics]]

## Related Concepts

- [[data-races]]
- [[ownership]]
- [[shadowing]]
- [[mutable-static-variables]]
