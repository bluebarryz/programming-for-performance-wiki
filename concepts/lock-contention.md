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
---

# Lock Contention

Most locking time is spent waiting for the lock to become available, not in the actual lock/unlock operations. Lock contention can be reduced by:

- Making locking regions smaller (more granular critical sections)
- Using more locks for independent sections

High contention serializes the program and is one of the main performance costs of locking. Using [[trylock]] can help measure contention. [[lock-convoys]] are an extreme manifestation of contention.

## Prerequisites

- [[locking-and-synchronization]] — Understanding how locks serialize thread access
- [[parallelism]] — Understanding why contention degrades parallel performance

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[critical-section-sizing]]
- [[locking-granularity]]
- [[lock-convoys]]
- [[trylock]]
