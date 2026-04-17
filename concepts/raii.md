---
tags:
  - concept
  - ECE459
  - L02
  - rust
  - memory
prerequisites:
  - "[[ownership]]"
---

# RAII (Resource Acquisition Is Initialization)

RAII is a pattern from C++ where a resource's lifetime is tied to the lifetime of a variable: the resource is acquired when the variable is created and released when the variable goes out of scope. Rust follows the same pattern through ownership -- when the owner goes out of scope, the value is dropped (deallocated).

The advantage of Rust's ownership over RAII in C++ is that the compiler *enforces* the "one owner" rule. In C++ you can violate the single-owner assumption and end up with dangling references and segfaults. In Rust, the compiler prevents this.

RAII also applies to Rust's `Mutex<T>`: the lock is automatically released when the `MutexGuard` goes out of scope, so you cannot forget to unlock.

## Prerequisites
- [[ownership]] — Rust implements RAII through the ownership system

## Lectures

- [[L02-Rust-Basics]]

## Related Concepts

- [[ownership]]
- [[rust-memory-management]]
- [[mutex]]
