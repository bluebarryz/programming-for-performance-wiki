---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[ownership]]"
  - "[[box-smart-pointer]]"
  - "[[copy-and-drop-traits]]"
---

# Rc (Reference Counting)

`Rc<T>` is Rust's single-threaded reference-counted smart pointer, enabling shared ownership. You create one with `Rc::new(value)` and make additional references with `clone()`, which increments the reference count rather than copying the data. The value is dropped only when the last reference goes away (count reaches zero). This is useful for data structures like graphs where multiple nodes need to point to the same data.

`Rc<T>` can leak memory if reference cycles form -- the count never reaches zero and the memory is never freed. Critically, `Rc<T>` does not implement the [[send-trait]] because its internal counter is not managed atomically, making it unsafe for multi-threaded use. For thread-safe shared ownership, use [[arc-atomic-reference-counting]] instead. Unlike C++'s `shared_ptr`, you cannot keep a raw reference to the value after the `Rc` is dropped.

## Prerequisites
- [[ownership]] — Rc enables shared ownership, relaxing the single-owner rule
- [[box-smart-pointer]] — Rc extends Box with shared ownership via reference counting
- [[copy-and-drop-traits]] — Rc's clone increments a counter rather than copying data; Drop decrements it

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[arc-atomic-reference-counting]]
- [[box-smart-pointer]]
- [[send-trait]]
