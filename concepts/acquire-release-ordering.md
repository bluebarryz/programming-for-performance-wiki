---
tags:
  - concept
  - ece459
  - memory-consistency
  - atomics
lectures:
  - L15
prerequisites:
  - "[[sequential-consistency]]"
  - "[[atomic-operations]]"
  - "[[locking-and-synchronization]]"
---

# Acquire-Release Ordering

Acquire-release ordering is a memory ordering model weaker than [[sequential-consistency]] but stronger than [[relaxed-ordering]]. Acquire means that no memory accesses (reads or writes) after the acquire operation can be reordered to before it. Release means no memory accesses before the release operation can be reordered to after it. Together, they "trap" operations between them, preventing them from escaping in either direction.

This pairing is ideal for implementing critical sections. Acquire at the start prevents operations from leaking out before the lock is taken; release at the end prevents them from leaking out after the lock is released. The Rustonomicon demonstrates this with a spinlock implementation using `Ordering::Acquire` on the `compare_and_swap` to take the lock and `Ordering::Release` on the `store` to release it.

Acquire-release does not provide a total global ordering of operations across all threads the way sequential consistency does. It only establishes a happens-before relationship between the releasing thread and the acquiring thread. This makes it cheaper to implement on hardware with weak memory models like ARM, potentially offering a performance edge over sequential consistency when you can prove correctness.

## Prerequisites

- [[sequential-consistency]] — Acquire-release is a weaker (cheaper) alternative to SeqCst
- [[atomic-operations]] — Acquire-release is a memory ordering for atomic operations
- [[locking-and-synchronization]] — Acquire-release models the lock/unlock pattern of critical sections

## Lectures

- [[L15-Memory-Consistency]]

## Related Concepts

- [[sequential-consistency]]
- [[relaxed-ordering]]
- [[memory-barriers]]
- [[memory-consistency-models]]
- [[atomic-operations]]
