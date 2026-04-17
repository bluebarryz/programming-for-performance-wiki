---
tags:
  - concept
  - ece459
  - L11
  - locking
  - performance
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[amdahls-law]]"
  - "[[data-races]]"
---

# Critical Section Sizing

Critical sections should be "as large as they need to be but no larger." They must contain all shared data accesses (both reads and writes) but should exclude any statements that do not operate on shared data. Extraneous statements inside a critical section unnecessarily increase the serial portion of the program, reducing opportunities for parallelism.

In Rust, a critical section lasts until the `MutexGuard` goes out of scope. To end it early, you can use manual scoping (a block `{ ... }`) so the guard is dropped at the end of the block, or explicitly call `drop()` on the guard. The producer-consumer example in the course shows how moving `consume_item()` and semaphore operations outside the critical section reduced runtime from ~2.8s to ~1.1s.

Keeping critical sections small is important for two reasons: it reduces the serial portion of the program (per Amdahl's Law), and it reduces contention for the lock resource itself.

## Prerequisites

- [[locking-and-synchronization]] — Understanding what locks are and why they exist
- [[amdahls-law]] — Explains why the serial portion (critical section size) limits speedup
- [[data-races]] — Motivates why critical sections are needed to protect shared data

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[locking-granularity]]
- [[lock-contention]]
- [[lock-overhead]]
