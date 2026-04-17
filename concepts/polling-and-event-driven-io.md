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

# Polling and Event-Driven I/O

There are two fundamental ways to check whether I/O is ready: polling (implemented via `select`, `poll`, and `epoll` on UNIX) and interrupts (signals). The [[mio-event-loop]] library abstracts over polling-based approaches across platforms -- `epoll` on Linux, IOCP on Windows, and `kqueue` on macOS/BSDs.

The basic workflow for event-driven I/O is: register interest in events on various sources (e.g., sockets), then enter a loop calling `poll()` which blocks until something happens or a timeout expires. When events arrive, you process them in the loop. This avoids dedicating a thread per connection and scales to thousands of concurrent connections. The [[libcurl-easy-and-multi]] multi interface is a practical example: you start multiple requests, then loop calling `perform()` and `wait()` to process them as they complete.

## Prerequisites
- [[blocking-vs-non-blocking-io]] — Polling is the mechanism that enables non-blocking I/O

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[blocking-vs-non-blocking-io]]
- [[mio-event-loop]]
- [[concurrent-server-architectures]]
