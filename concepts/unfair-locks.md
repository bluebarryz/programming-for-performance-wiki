---
tags:
  - concept
  - ece459
  - L12
  - locking
  - performance
prerequisites:
  - "[[lock-contention]]"
  - "[[lock-convoys]]"
---

# Unfair Locks

An unfair lock does not hand ownership directly to a waiting thread when released. Instead, the lock becomes unowned, and the scheduler picks the next thread to run. If that thread wants the lock, it gets it; otherwise, some other thread may acquire it first.

This contrasts with fair locks (Windows XP and earlier), where a waiting thread B would receive ownership immediately when thread A released the lock. Fair locks cause [[lock-convoys]] because B owns the lock but isn't running yet, and the context switch delay (4,000-10,000 cycles on Windows) means the lock is held but unused.

Unfair locks risk starvation in theory, but in practice this is unlikely. Windows mitigates it by temporarily boosting the priority of unblocked threads.

## Prerequisites

- [[lock-contention]] — Understanding why contention makes fair lock handoff expensive
- [[lock-convoys]] — Unfair locks are the root fix for the lock convoy problem

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[lock-convoys]]
- [[lock-contention]]
