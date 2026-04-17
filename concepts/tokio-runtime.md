---
tags:
  - concept
  - ece459
  - async
lectures:
  - L05
prerequisites:
  - "[[futures-and-async-await]]"
  - "[[mio-event-loop]]"
---

# Tokio Runtime

Tokio is an asynchronous runtime for Rust that provides a sophisticated executor for [[futures-and-async-await]]. When there are multiple active awaits, Tokio can multiplex them onto different threads. You specify the Tokio executor by annotating your `main()` function with `#[tokio::main]` and declaring it `async`, instead of manually calling `block_on`. Other executors (e.g., `async_std`) exist as alternatives.

Tokio builds on top of [[mio-event-loop]] for low-level non-blocking I/O. It also provides async-aware versions of standard library types, such as `tokio::fs` for async file I/O. The course uses Tokio as the primary async runtime for demonstrating non-blocking network programming in Rust.

## Prerequisites
- [[futures-and-async-await]] — Tokio is an executor for futures and async/await
- [[mio-event-loop]] — Tokio builds on mio for low-level non-blocking I/O

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[futures-and-async-await]]
- [[mio-event-loop]]
- [[blocking-vs-non-blocking-io]]
