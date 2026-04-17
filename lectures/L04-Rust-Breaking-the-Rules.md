---
tags:
  - lecture
  - ECE459
  - rust
  - unsafe
lecture: L04
title: "Rust: Breaking the Rules for Fun and Performance"
prerequisite_lectures:
  - "[[L03-Rust-Borrowing-Slices-Threads-Traits]]"
---

# L04 - Rust: Breaking the Rules for Fun and Performance

This lecture covers mechanisms for breaking Rust's strict ownership and borrowing rules when necessary. It starts with smart pointers: `Box<T>` for heap allocation, `Rc<T>` for single-threaded shared ownership via reference counting, and `Arc<T>` for thread-safe atomic reference counting. It then covers lifetimes and lifetime annotations, including the `'static` lifetime. The lecture introduces `unsafe` Rust: what an unsafe block permits (calling unsafe functions, accessing mutable statics, implementing unsafe traits, accessing union fields, dereferencing raw pointers), unsafe functions and traits, mutable static variables, unions, and raw pointers. It concludes with common Rust pitfalls and advice on using libraries.

## Prerequisite Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]] — Borrowing rules and threads that this lecture relaxes with smart pointers and unsafe

## Concepts Covered

- [[box-smart-pointer]]
- [[rc-reference-counting]]
- [[arc-atomic-reference-counting]]
- [[lifetimes]]
- [[static-lifetime]]
- [[unsafe-rust]]
- [[raw-pointers]]
- [[unions]]
- [[mutable-static-variables]]
- [[rust-pitfalls]]
- [[mutex]]
