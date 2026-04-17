---
tags:
  - lecture
  - ECE459
  - async
  - io
lecture: L05
title: Asynchronous I/O
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
---

# L05 - Asynchronous I/O

This lecture motivates non-blocking I/O by showing that blocking `read` calls waste CPU cycles. It introduces the `mio` library for low-level event-driven I/O using `Poll`, event registration, and event loops. Network programming with `reqwest` (blocking and non-blocking) is covered, followed by futures and `async`/`await` in Rust. The lecture explains plug-in executors (`futures::executor::block_on` vs `tokio`). It then covers `libcurl` bindings: the synchronous `easy` interface with callbacks, and the asynchronous `multi` interface for concurrent HTTP requests. Finally, it compares four server architecture choices: blocking I/O with 1 process per request, blocking I/O with 1 thread per request, async I/O with thread pool and callbacks, and non-blocking I/O with select/poll.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Latency, bandwidth, and the performance motivation for non-blocking approaches

## Concepts Covered

- [[blocking-vs-non-blocking-io]]
- [[mio-event-loop]]
- [[polling-and-event-driven-io]]
- [[futures-and-async-await]]
- [[tokio-runtime]]
- [[libcurl-easy-and-multi]]
- [[callbacks]]
- [[concurrent-server-architectures]]
