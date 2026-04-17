---
tags:
  - concept
  - ece459
  - async
lectures:
  - L05
prerequisites:
  - "[[blocking-vs-non-blocking-io]]"
---

# Futures and Async/Await

A future in Rust is an object that will, at some point, produce a value. The analogy from the course: you order a bicycle but the shop is out of stock, so they give you a ticket (the future). Later, you trade the ticket (await) for the actual bicycle. In code, calling an `async fn` returns a future rather than executing immediately. The `.await` keyword suspends the current task until the future resolves.

Rust uses a plug-in executor model for async/await -- the language defines the syntax but not the runtime. The simplest executor is `futures::executor::block_on`, which just blocks the current thread. The [[tokio-runtime]] provides a more sophisticated executor that can multiplex multiple active awaits onto different threads. You opt into Tokio by annotating `main()` with `#[tokio::main]` and making it `async`. There are also other executors like `async_std`.

## Prerequisites
- [[blocking-vs-non-blocking-io]] — Async/await is a high-level abstraction over non-blocking I/O

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[tokio-runtime]]
- [[blocking-vs-non-blocking-io]]
- [[callbacks]]
