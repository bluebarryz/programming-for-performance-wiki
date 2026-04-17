---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[unsafe-rust]]"
  - "[[data-races]]"
  - "[[immutability-by-default]]"
---

# Mutable Static Variables

Rust strongly discourages global variables, but you can make them mutable using `static mut`. Accessing or modifying a mutable static variable requires an `unsafe` block because global mutable state is inherently prone to data races -- any thread can access it from anywhere. In production code, global variables are not recommended due to the software engineering risks.

The course acknowledges that mutable statics are used frequently in assignments, exercises, labs, and exam questions as a convenient shortcut for passing shared state to threads. However, the proper approach is to pass [[mutex]] and queue constructs from the main thread to newly created threads, rather than relying on global state.

## Prerequisites
- [[unsafe-rust]] — Accessing mutable statics requires an unsafe block
- [[data-races]] — Mutable statics are dangerous because any thread can access them, risking races
- [[immutability-by-default]] — Mutable statics are an exception to Rust's default immutability

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[unsafe-rust]]
- [[mutex]]
- [[arc-atomic-reference-counting]]
