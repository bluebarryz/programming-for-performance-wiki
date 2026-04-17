---
tags:
  - concept
  - ece459
  - L11
  - locking
  - performance
prerequisites:
  - "[[locking-and-synchronization]]"
---

# Lock Overhead

Using a lock is not free. The costs include:

- Allocated memory for the lock
- Initialization and destruction time
- Acquisition and release time

These costs scale with the number of locks. This is a key consideration in the [[locking-granularity]] trade-off: fine-grained locking increases overhead proportional to the number of locks.

## Prerequisites

- [[locking-and-synchronization]] — Understanding what locks are and their basic costs

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[locking-granularity]]
- [[lock-contention]]
- [[fine-grained-locking]]
