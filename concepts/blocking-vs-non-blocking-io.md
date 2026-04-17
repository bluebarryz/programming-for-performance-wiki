---
tags:
  - concept
  - ece459
  - async
lectures:
  - L05
prerequisites:
  - "[[parallelism]]"
  - "[[bandwidth-vs-latency]]"
---

# Blocking vs Non-Blocking I/O

Blocking I/O means a program halts execution while waiting for an I/O operation (e.g., reading a file or network socket) to complete. The CPU sits idle during this time, wasting cycles. Threads can mitigate this -- while one thread blocks on I/O, others can run -- but threads bring their own costs: potential race conditions, per-thread stack overhead, and limits on maximum thread count.

Non-blocking I/O allows the program to continue doing useful work while I/O is in progress. The program initiates the I/O operation and checks back later for results, either through polling (select/poll/epoll) or event-driven mechanisms. This is the foundation of asynchronous I/O and is critical for building high-performance servers that handle many concurrent connections without dedicating a thread to each one.

## Prerequisites
- [[parallelism]] — Non-blocking I/O is an alternative to threads for handling concurrent work
- [[bandwidth-vs-latency]] — Non-blocking I/O improves throughput by avoiding idle CPU during waits

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[polling-and-event-driven-io]]
- [[concurrent-server-architectures]]
- [[mio-event-loop]]
- [[futures-and-async-await]]
