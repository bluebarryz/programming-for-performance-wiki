---
tags:
  - concept
  - ece459
  - L11
  - locking
  - performance
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[parallelism]]"
  - "[[deadlocks]]"
---

# Locking Granularity

Lock granularity refers to how much data is protected by a given lock. It is a spectrum with trade-offs at each end:

- **Coarse-grained locking**: fewer, bigger locks. Easier to implement, no deadlock risk with a single lock, but limits parallelism.
- **Fine-grained locking**: many smaller locks protecting smaller sections. Maximizes parallelism but increases overhead, complexity, and deadlock risk.

Three major concerns when choosing granularity:
1. **Overhead** -- locks cost memory, initialization/destruction time, and acquisition/release time.
2. **Contention** -- threads waiting for locks waste time; smaller or more locks reduce contention.
3. **Deadlocks** -- more locks means more potential for deadlock.

Database locking is a classic example: locks can be at the field, record, or table level, ranging from fine to coarse.

## Prerequisites

- [[locking-and-synchronization]] — Understanding what locks are and how they work
- [[parallelism]] — Understanding why we want threads to run concurrently
- [[deadlocks]] — Knowing what deadlock is, since granularity affects deadlock risk

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[coarse-grained-locking]]
- [[fine-grained-locking]]
- [[lock-overhead]]
- [[lock-contention]]
- [[deadlock]]
