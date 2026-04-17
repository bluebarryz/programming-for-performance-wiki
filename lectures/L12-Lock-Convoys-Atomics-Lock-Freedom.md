---
tags:
  - lecture
  - ece459
  - lock-convoys
  - atomics
  - lock-freedom
lecture: L12
title: "Lock Convoys, Atomics, Lock-Freedom"
prerequisite_lectures:
  - "[[L11-Use-of-Locks-Reentrancy]]"
---

# L12 -- Lock Convoys, Atomics, Lock-Freedom

This lecture introduces the lock convoy problem -- a performance pathology where threads contending for a lock end up moving in lockstep, wasting CPU time on context switches. It covers unfair locks as a solution (used since Windows Vista), and mitigation strategies (sleep, share, cache, trylock). The lecture then introduces atomic operations as a lower-overhead alternative to locks, including compare-and-swap (CAS) and the ABA problem. Finally, it covers lock-free and wait-free data structures, their definitions, trade-offs, and examples in Rust.

## Prerequisite Lectures
- [[L11-Use-of-Locks-Reentrancy]] — Lock mechanics, contention, and deadlock concepts that lock convoys and atomics build upon

## Concepts Covered

- [[lock-convoys]]
- [[unfair-locks]]
- [[thundering-herd-problem]]
- [[lost-wakeup-problem]]
- [[atomic-operations]]
- [[compare-and-swap]]
- [[spinlock]]
- [[aba-problem]]
- [[lock-free-data-structures]]
- [[wait-free-data-structures]]
- [[non-blocking-data-structures]]
