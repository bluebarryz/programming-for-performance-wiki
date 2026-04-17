---
tags:
  - concept
  - ece459
  - rust
  - concurrency
lectures:
  - L03
prerequisites:
  - "[[traits]]"
  - "[[borrowing-and-references]]"
  - "[[rust-threads]]"
---

# Sync Trait

The `Sync` trait means that a type can be safely referenced from multiple threads simultaneously. Primitive types have this trait, as do programmer-defined types composed entirely of `Sync` types. Importantly, `Sync` does not mean all operations on the type are race-free -- it means that *references* to the type can exist in different threads concurrently. You still cannot have multiple mutable references, so if you want more than one thread to modify the value, you need [[mutex]] for mutual exclusion.

If you implement `Sync` manually (not by composition), you must tag your implementation with `unsafe` and ensure the safety conditions yourself. Getting this wrong has caused many unsound Rust bugs. For most use cases, the automatically derived `Sync` implementation is sufficient.

## Prerequisites
- [[traits]] — Sync is a trait; understanding the trait system is needed
- [[borrowing-and-references]] — Sync governs whether references can be shared across threads
- [[rust-threads]] — Sync is relevant when multiple threads access the same data

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[send-trait]]
- [[traits]]
- [[mutex]]
- [[unsafe-rust]]
