---
tags:
  - concept
  - ece459
  - L12
  - L15
  - concurrency
  - locking
prerequisites:
  - "[[compare-and-swap]]"
  - "[[atomic-operations]]"
  - "[[locking-and-synchronization]]"
---

# Spinlock

A spinlock continuously attempts to acquire a lock in a loop (busy-waiting) rather than blocking the thread. It makes sense when the expected wait time is less than the cost of two context switches.

A spinlock can be implemented using [[compare-and-swap]] on an `AtomicBool`:
```rust
while my_lock.compare_and_swap(false, true, Ordering::SeqCst) == true {
    spin_loop_hint();
}
// critical section
my_lock.store(false, Ordering::SeqCst);
```

The `spin_loop_hint()` call tells the CPU it can switch to another hyperthread or enter a lower-power mode during the spin.

Spinlocks are non-blocking but are *not* lock-free: if the thread holding the lock is suspended, all spinning threads are stuck. In [[L15-Memory-Consistency]], a spinlock is also shown using [[acquire-release-ordering]] for better performance than [[sequential-consistency]].

## Prerequisites

- [[compare-and-swap]] — Spinlocks are implemented using CAS loops
- [[atomic-operations]] — Spinlocks rely on atomic state to coordinate threads
- [[locking-and-synchronization]] — Understanding the blocking lock alternative that spinlocks replace

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]
- [[L15-Memory-Consistency]]

## Related Concepts

- [[compare-and-swap]]
- [[atomic-operations]]
- [[lock-free-data-structures]]
- [[acquire-release-ordering]]
