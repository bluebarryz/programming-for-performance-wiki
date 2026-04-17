---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[rust-motivation]]"
---

# Result and Error Handling

In Rust, many functions return `Result` types, which are either `Ok` with the expected value or `Err` with an error description. To extract the value, you must handle the result explicitly. There are three main approaches: a `match` expression (like a switch statement), `unwrap()` which panics on error, and `expect()` which panics with a custom message.

Using `unwrap()` everywhere is tempting but dangerous. The Cloudflare outage of November 2025 was traced to an `unwrap()` call with no error checking, causing a panic that took down services for many customers. The `expect()` function is preferred because it provides a descriptive error message for debugging. It is also recommended to use `Result` types for your own functions to give callers the information they need.

Rust does not have exceptions. There is a performance trade-off: exceptions that do not fire (the happy path) are faster than explicitly handling error codes or `Result` types, but Rust forces you to always pay this cost. Simulating exceptions with `panic!` is not a best practice.

## Prerequisites
- [[rust-motivation]] — Rust's error handling via Result types is part of its safety-first design

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[rust-pitfalls]]
