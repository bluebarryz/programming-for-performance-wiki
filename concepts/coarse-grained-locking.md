---
tags:
  - concept
  - ece459
  - L11
  - locking
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[parallelism]]"
---

# Coarse-Grained Locking

Coarse-grained locking uses few locks (perhaps just one) to protect large sections of the program. Advantages:

- Easier to implement
- No deadlock risk with a single lock
- Lowest memory usage and setup time

The major disadvantage is that the parallel program quickly becomes sequential, since all threads must serialize on the single lock.

A notable example is Python's [[global-interpreter-lock]], which puts a lock around the entire interpreter. OS kernels have also used "big kernel locks" (e.g., Linux until ~2011).

## Prerequisites

- [[locking-and-synchronization]] — Understanding basic lock mechanics
- [[parallelism]] — Understanding what parallelism we lose with coarse locking

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[locking-granularity]]
- [[fine-grained-locking]]
- [[global-interpreter-lock]]
- [[lock-contention]]
