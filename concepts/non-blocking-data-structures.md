---
tags:
  - concept
  - ece459
  - L12
  - concurrency
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[atomic-operations]]"
---

# Non-Blocking Data Structures

A non-blocking data structure is one where none of the operations can result in the calling thread being blocked. This is a broad category:

- [[lock-free-data-structures]] are always non-blocking (if one thread is suspended, others can still make progress).
- A [[spinlock]] or busy-wait approach is non-blocking (the thread never truly blocks) but is *not* lock-free, because a suspended lock holder prevents others from completing.
- Concurrency-controlled data structures in languages like Java may handle locking internally but can still be blocking.

Non-blocking is a necessary but not sufficient condition for lock-freedom.

## Prerequisites

- [[locking-and-synchronization]] — Understanding blocking vs non-blocking thread behavior
- [[atomic-operations]] — Non-blocking structures use atomics to avoid blocking

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[lock-free-data-structures]]
- [[wait-free-data-structures]]
- [[spinlock]]
