---
tags:
  - concept
  - ece459
  - L11
  - locking
  - python
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[parallelism]]"
---

# Global Interpreter Lock

The Global Interpreter Lock (GIL) is an example of [[coarse-grained-locking]] taken to the extreme: Python puts a single lock around the entire interpreter. This is the main reason most scripting languages have poor parallel performance.

Implications:

- The only performance benefit from threading is when threads are waiting for I/O.
- Any non-I/O-bound threaded program will be *slower* than the sequential version, plus the interpreter adds overhead.

The GIL illustrates the trade-off of coarse-grained locking: correctness is easy to achieve, but parallelism is effectively eliminated.

## Prerequisites

- [[locking-and-synchronization]] — Understanding what a lock is
- [[parallelism]] — Understanding the parallelism the GIL prevents

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[coarse-grained-locking]]
- [[locking-granularity]]
- [[lock-contention]]
