---
tags:
  - lecture
  - ECE459
  - rust
  - concurrency
lecture: L03
title: "Rust: Borrowing, Slices, Threads, Traits"
prerequisite_lectures:
  - "[[L02-Rust-Basics]]"
---

# L03 - Rust: Borrowing, Slices, Threads, Traits

This lecture covers borrowing and references as an alternative to transferring ownership. It explains immutable vs mutable references, the borrow checker's rules (one mutable XOR many immutable references), dangling references, and non-lexical lifetimes. It then covers slices as references into contiguous subsets of collections. Error handling with `Result`, `unwrap()`, and `expect()` is discussed. The second half introduces Rust's fearless concurrency model: spawning threads, closures, capturing variables (borrowing vs `move`), message passing via channels (mpsc), and the `Send`, `Sync`, and `Iterator` traits. Finally, it introduces `Mutex<T>` and the problem of sharing a mutex across threads.

## Prerequisite Lectures
- [[L02-Rust-Basics]] — Ownership and move semantics that borrowing builds upon

## Concepts Covered

- [[borrowing-and-references]]
- [[mutable-references]]
- [[borrow-checker]]
- [[non-lexical-lifetimes]]
- [[slices]]
- [[result-and-error-handling]]
- [[fearless-concurrency]]
- [[rust-threads]]
- [[closures-and-capturing]]
- [[move-keyword]]
- [[message-passing-channels]]
- [[send-trait]]
- [[sync-trait]]
- [[iterator-trait]]
- [[traits]]
- [[mutex]]
