---
tags:
  - concept
  - ece459
  - L12
  - concurrency
  - lock-freedom
prerequisites:
  - "[[compare-and-swap]]"
  - "[[atomic-operations]]"
  - "[[locking-and-synchronization]]"
---

# Lock-Free Data Structures

A lock-free data structure uses no locks and guarantees that if any thread performing an operation is suspended, other threads can still complete their tasks. This is distinct from merely being non-blocking (e.g., a [[spinlock]] is non-blocking but not lock-free, since a suspended lock holder blocks everyone).

Key properties:
- No locks are used
- Thread-safe: concurrent access produces correct results
- Forward progress is guaranteed system-wide (though individual threads may need to retry)

Use cases: when you must guarantee progress, when locks can't be used (e.g., signal handlers), or when a thread dying with a lock would hang the system.

Lock-free structures typically use [[compare-and-swap]] loops. A classic example is a lock-free stack where `push` uses CAS to atomically update the head pointer, retrying on failure.

Lock-free algorithms are not necessarily faster than lock-based ones -- they are about ensuring forward progress, not speed. They may be slower but are used when the guarantees are needed.

## Prerequisites

- [[compare-and-swap]] — Lock-free structures are built on CAS retry loops
- [[atomic-operations]] — Lock-free structures use atomics instead of locks
- [[locking-and-synchronization]] — Understanding the lock-based alternative and its limitations

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[wait-free-data-structures]]
- [[non-blocking-data-structures]]
- [[compare-and-swap]]
- [[aba-problem]]
- [[atomic-operations]]
