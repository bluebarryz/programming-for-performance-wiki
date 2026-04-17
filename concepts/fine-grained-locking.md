---
tags:
  - concept
  - ece459
  - L11
  - locking
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[deadlocks]]"
  - "[[parallelism]]"
---

# Fine-Grained Locking

Fine-grained locking divides locks to protect smaller sections of data, maximizing parallelization. Disadvantages include:

- Wasted memory and setup time if the program isn't very parallel
- Increased risk of deadlocks
- More error-prone (must grab the correct lock)

Examples include databases that can lock at the field, record, or table level, and locking individual objects (though transactional guarantees may be needed).

## Prerequisites

- [[locking-and-synchronization]] — Understanding basic lock mechanics
- [[deadlocks]] — More locks means more deadlock risk
- [[parallelism]] — Understanding the parallelism gains fine-grained locking enables

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[locking-granularity]]
- [[coarse-grained-locking]]
- [[deadlock]]
- [[lock-overhead]]
