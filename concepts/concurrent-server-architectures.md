---
tags:
  - concept
  - ece459
  - async
lectures:
  - L05
prerequisites:
  - "[[blocking-vs-non-blocking-io]]"
  - "[[parallelism]]"
  - "[[polling-and-event-driven-io]]"
---

# Concurrent Server Architectures

The course identifies four main architectures for servers handling concurrent socket I/O, the first two blocking and the latter two non-blocking:

1. **Blocking I/O, 1 process per request** -- the old Apache model. The main thread forks a new process for each connection. Simple to program but scales poorly (~10,000 processes max) with high overhead.
2. **Blocking I/O, 1 thread per request** -- same idea but with threads instead of processes. Lower overhead than processes but still limited in scale, and introduces race conditions on shared data.
3. **Asynchronous I/O, thread pool with callbacks** -- threads are multiplexed across connections. Each thread handles multiple connections using callbacks for I/O completion.
4. **Non-blocking I/O, thread pool with select/poll, event-driven** -- threads handle multiple connections using [[polling-and-event-driven-io]], the most scalable approach.

Performance data from lighttpd showed that linux-aio-sendfile achieved 72.70 fetches/sec versus 36.45 for blocking sendfile, with significantly higher CPU idle time (46% vs 16%), demonstrating the efficiency gains of asynchronous I/O.

## Prerequisites
- [[blocking-vs-non-blocking-io]] — The four architectures are distinguished by blocking vs non-blocking I/O
- [[parallelism]] — Server architectures use processes or threads for parallel request handling
- [[polling-and-event-driven-io]] — The most scalable architecture uses event-driven I/O

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[blocking-vs-non-blocking-io]]
- [[polling-and-event-driven-io]]
- [[callbacks]]
