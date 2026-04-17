---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[tracing]]"
---

# Tracing Overhead

The overhead of tracing varies enormously depending on what is being recorded. Some quick off-the-cuff figures from the course: tracking every conditional branch results in about a 20x slowdown (acceptable only on development machines, never in production). Timestamping every function call and return causes a 1.2-1.5x slowdown (possibly acceptable in production temporarily for non-time-critical tasks). Timestamping every system call entry and exit is less than 1% overhead (acceptable in production for all but the most time-critical operations and could remain in place permanently).

Disk trace tools have extremely tiny overhead because the disk is very slow compared to the CPU. Similarly, network tracing has low relative overhead due to network latency. The general principle is that the closer the tracing is to the CPU's speed, the higher the relative overhead. Developers must be judicious about how much trace data to capture, balancing the need for information against the performance cost and storage requirements.

## Prerequisites
- [[tracing]] — Overhead figures are meaningless without understanding what tracing records

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[tracing]]
- [[observability]]
- [[valgrind]]
- [[logging]]
