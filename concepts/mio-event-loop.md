---
tags:
  - concept
  - ece459
  - async
lectures:
  - L05
prerequisites:
  - "[[blocking-vs-non-blocking-io]]"
  - "[[polling-and-event-driven-io]]"
---

# Mio Event Loop

`mio` is a low-level I/O library from the Tokio project that provides a cross-platform event loop for non-blocking I/O. It abstracts over OS-specific polling mechanisms (`epoll`, IOCP, `kqueue`) behind a unified API. The workflow has three steps: create a `Poll` instance, register event sources (like `TcpListener`) with it, and wait for events in a loop with `Poll::poll()`.

When registering an event source, you specify what you are interested in (e.g., `Interest::READABLE`), a token to identify which source triggered the event, and the source itself. In the event loop, `poll.poll()` populates an `Events` collection and blocks for up to the specified timeout. You then iterate over events, match on the token, and handle each one. The `would_block` error kind indicates there is no more data to read right now, which is normal in non-blocking I/O. Higher-level abstractions like [[tokio-runtime]] build on mio.

## Prerequisites
- [[blocking-vs-non-blocking-io]] — Mio implements non-blocking I/O via an event loop
- [[polling-and-event-driven-io]] — Mio abstracts over OS-specific polling mechanisms

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[polling-and-event-driven-io]]
- [[blocking-vs-non-blocking-io]]
- [[tokio-runtime]]
