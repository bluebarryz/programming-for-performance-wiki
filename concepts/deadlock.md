---
tags:
  - concept
  - ece459
  - L11
  - locking
  - concurrency
prerequisites:
  - "[[deadlocks]]"
  - "[[locking-and-synchronization]]"
---

# Deadlock

Deadlock occurs when threads are stuck waiting for each other to release locks. The four necessary conditions are:

1. **Mutual Exclusion** -- a resource belongs to at most one process at a time.
2. **Hold-and-Wait** -- a process holding resources may request additional ones and be forced to wait.
3. **No Preemption** -- a resource can only be released by the process holding it.
4. **Circular-Wait** -- a cycle exists in the resource allocation graph.

Two main strategies to avoid deadlock:

1. **Consistent lock ordering** -- assign a total order to locks and always acquire in that order. This can be proven to prevent circular-wait by contradiction.
2. **Trylock** -- use non-blocking lock attempts. If a lock can't be acquired, release held locks and retry. This breaks the hold-and-wait condition.

When locks "travel with data" (e.g., bank accounts), consistent ordering can be achieved by ordering on an immutable field like an account number.

## Prerequisites

- [[deadlocks]] — L01 introduction to the concept of deadlock
- [[locking-and-synchronization]] — Understanding lock acquisition and release mechanics

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[locking-granularity]]
- [[trylock]]
- [[fine-grained-locking]]
- [[lock-contention]]
