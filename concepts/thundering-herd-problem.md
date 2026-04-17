---
tags:
  - concept
  - ece459
  - L12
  - concurrency
  - performance
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[lock-contention]]"
---

# Thundering Herd Problem

The thundering herd problem occurs when a condition is fulfilled (e.g., a broadcast on a condition variable) and a large number of threads wake up simultaneously to take action. Most of them can't all proceed, so they get blocked again, only to be awakened all at once in the future. This wastes CPU time on context switches and scheduling.

The solution is to wake threads one at a time instead of all at once. However, this introduces the risk of the [[lost-wakeup-problem]].

Similar to [[lock-convoys]] in that it involves many threads contending inefficiently, but the mechanism is different: thundering herd is triggered by a broadcast wakeup, not by lock handoff.

## Prerequisites

- [[locking-and-synchronization]] — Understanding condition variables and thread wakeup mechanics
- [[lock-contention]] — Thundering herd is a form of contention caused by broadcast wakeups

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[lock-convoys]]
- [[lost-wakeup-problem]]
