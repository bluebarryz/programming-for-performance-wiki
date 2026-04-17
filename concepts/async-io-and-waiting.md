---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[blocking-vs-non-blocking-io]]"
  - "[[futures-and-async-await]]"
  - "[[locking-and-synchronization]]"
---

# Async I/O and Waiting

In the context of software architecture, excessive waiting is a performance pitfall that can be addressed through asynchronous I/O. Rather than blocking on each operation and waiting for its result before starting the next, async I/O allows operations to be initiated and their results collected later. This eliminates unnecessary waits and enables multiple I/O requests to execute in parallel, reducing total completion time.

Beyond raw performance, an asynchronous model improves perceived responsiveness. By returning partial results sooner and loading the rest later, the response time -- the time to get *some* result back -- is reduced. This is the principle behind modern web pages where the main content loads immediately while secondary panels show loading indicators.

A related form of excessive waiting is lock contention. When every thread must acquire the same lock (e.g., an `Arc<Mutex<Vector>>`) to add data, performance suffers from serialization. This can be alleviated by switching to a message-passing model: one thread owns the data and others send updates via channels. While channels have their own overhead, it is offset by eliminating lock contention entirely.

## Prerequisites

- [[blocking-vs-non-blocking-io]] — Async I/O from L05 is the foundation for eliminating excessive waiting
- [[futures-and-async-await]] — The async/await model from L05 is the implementation mechanism
- [[locking-and-synchronization]] — Lock contention is a form of excessive waiting that async can address

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[locking-and-synchronization]]
- [[thread-pools]]
- [[system-design]]
