---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[unsafe-rust]]"
  - "[[borrowing-and-references]]"
---

# Raw Pointers

Raw pointers in Rust (`*const T` and `*mut T`) are like C pointers -- they have no ownership or borrowing guarantees. You can create raw pointers anywhere (creating them is safe), but dereferencing them requires an `unsafe` block because the compiler cannot verify they point to valid memory. Creating a raw pointer that is never dereferenced cannot crash your program; only using one can.

Raw pointers are needed for writing to specific memory addresses (e.g., memory-mapped I/O) and for calling into C libraries via FFI. You create them by casting references: `let r1 = &num as *const i32`. You can also cast an integer to a raw pointer for direct memory address access, such as `let add = 0xDEADBEEF` cast to `*const`. The Rust ecosystem of crates is growing, but sometimes you must interact with C libraries, and raw pointers are how you bridge that gap.

## Prerequisites
- [[unsafe-rust]] — Dereferencing raw pointers requires an unsafe block
- [[borrowing-and-references]] — Raw pointers bypass the safety guarantees of Rust references

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[unsafe-rust]]
- [[unions]]
