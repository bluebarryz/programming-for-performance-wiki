---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[observability]]"
---

# Tracing

Traces are recordings of the sequence of events in a program's execution, allowing developers to understand runtime behavior and reconstruct how the system reached a particular state. Tracing can cover CPU operations, memory access, disk I/O, network activity, and lock contention.

Tracing is useful for identifying deadlocks and delays caused by lock contention -- rather than logging every lock and unlock, the interesting cases are where threads fail to acquire a lock because another thread holds it. The trace itself takes up space: a main memory system with 20 GB/s bandwidth recording 8 bytes per 64-byte cache line can produce 2.4 GB of trace data per second, which would fill an 8 TB drive in under an hour. This means either capturing less data (recording fewer things) or recording for shorter periods. The [[tracing-overhead]] varies dramatically depending on what is being traced.

## Prerequisites
- [[observability]] — Tracing is one of the three core observability approaches

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[tracing-overhead]]
- [[observability]]
- [[logging]]
- [[counters]]
- [[valgrind]]
