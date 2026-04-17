---
tags:
  - concept
  - ece459
  - L11
  - L12
  - locking
  - concurrency
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[deadlocks]]"
---

# Trylock

Trylock is a non-blocking lock acquisition attempt. If the lock is unavailable, the calling thread is not blocked -- it returns immediately with a failure indication. In Rust, this is `try_lock()` on a `Mutex`, which returns `Ok` if successful and `Err` otherwise.

Trylock is useful for:

- **Deadlock avoidance** -- if you can't get all locks you need, release what you have and try again. This breaks the hold-and-wait condition.
- **Measuring lock contention** -- frequent trylock failures indicate high contention.
- **Mitigating lock convoys** -- try to acquire the lock, yield on failure, and fall back to a blocking lock after a retry limit. Even a spin limit of 2 can allow two threads to recover from contention without forming a convoy.

## Prerequisites

- [[locking-and-synchronization]] — Understanding blocking lock acquisition that trylock avoids
- [[deadlocks]] — Understanding the deadlock problem that trylock helps solve

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]
- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[deadlock]]
- [[lock-contention]]
- [[lock-convoys]]
