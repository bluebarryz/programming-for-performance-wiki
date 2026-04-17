---
tags:
  - concept
  - ECE459
  - L02
  - rust
  - memory
prerequisites:
  - "[[rust-motivation]]"
---

# Rust Memory Management

In C, memory management is fully manual (malloc/free). In Java, it is partly manual (explicit allocation, garbage-collected deallocation). C++ supports RAII. Rust does the same as C++ via RAII but with compile-time guarantees through [[ownership]].

Why not garbage collection? Two costs:
1. **Runtime overhead** -- the GC runtime must track allocations and decide when to collect.
2. **Collection cost** -- the GC can pause the program ("stop the world"), reorganize memory, and do so whenever it wants, for as long as it wants. This is bad for performance and predictability.

You don't pay GC costs in Rust. You do still pay for heap allocation and deallocation, but Rust makes it easier to allocate on the stack, which can improve performance. In general, C++ and Rust memory management overhead is comparable.

## Prerequisites
- [[rust-motivation]] — Understanding why Rust exists motivates its memory management approach

## Lectures

- [[L02-Rust-Basics]]

## Related Concepts

- [[ownership]]
- [[garbage-collection-vs-ownership]]
- [[raii]]
- [[rc-reference-counting]]
- [[arc-atomic-reference-counting]]
