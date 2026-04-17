---
tags:
  - concept
  - ece459
  - L12
  - locking
  - performance
prerequisites:
  - "[[lock-contention]]"
  - "[[locking-and-synchronization]]"
---

# Lock Convoys

A lock convoy is a performance pathology where two or more threads at the same priority frequently acquire a synchronization object, resulting in a "traffic jam." It occurs when a thread's quantum expires while it holds a lock, causing all other threads that need the lock to queue up. Each thread then takes a tiny step forward before blocking, spending most CPU time on context switches rather than useful work. Also called the "boxcar" problem.

Diagnosing a lock convoy: look for a lock with waiting threads but no apparent owner -- this indicates a handover is in progress.

Mitigation strategies:
- **Sleep** -- non-convoy threads call `sleep()` to yield time (band-aid solution)
- **Share** -- use [[reader-writer locks|unfair-locks]] or break critical sections into smaller ones
- **Cache** -- shrink critical section to just copy shared data, then operate on the copy
- **Trylock** -- use [[trylock]] with yield and a retry limit; even a spin limit of 2 can prevent convoy formation

The root fix is [[unfair-locks]], used since Windows Vista.

## Prerequisites

- [[lock-contention]] — Lock convoys are an extreme form of lock contention
- [[locking-and-synchronization]] — Understanding how lock acquisition and context switches interact

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[unfair-locks]]
- [[lock-contention]]
- [[trylock]]
- [[thundering-herd-problem]]
