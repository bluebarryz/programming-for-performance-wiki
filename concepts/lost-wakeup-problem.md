---
tags:
  - concept
  - ece459
  - L12
  - concurrency
prerequisites:
  - "[[locking-and-synchronization]]"
---

# Lost Wakeup Problem

The lost wakeup problem occurs when using `notify_one()` on a condition variable. If only one thread is woken and it fails to wake the next thread (or the wrong thread is woken), other threads that should proceed remain blocked indefinitely.

The general recommendation is to use `notify_all()` in all situations to avoid this problem, even though it can cause the [[thundering-herd-problem]]. Counting on each thread to unconditionally wake the next is considered too fragile.

In Rust, condition variables are available as `std::sync::Condvar` with `notify_one()` and `notify_all()` methods.

## Prerequisites

- [[locking-and-synchronization]] — Understanding condition variables and notify_one/notify_all semantics

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[thundering-herd-problem]]
