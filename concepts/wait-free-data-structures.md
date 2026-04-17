---
tags:
  - concept
  - ece459
  - L12
  - concurrency
  - lock-freedom
prerequisites:
  - "[[lock-free-data-structures]]"
  - "[[atomic-operations]]"
---

# Wait-Free Data Structures

A wait-free data structure guarantees that each thread will complete its operation within a bounded number of steps, regardless of what other threads do. This is a stronger guarantee than [[lock-free-data-structures]], where a particularly unlucky thread could theoretically retry forever.

A CAS retry loop with unbounded retries is lock-free but *not* wait-free. An atomic `fetch_add` operation, however, is wait-free because it always completes in a bounded number of steps:
```rust
fn increment_counter(ctr: &AtomicI32) {
    ctr.fetch_add(1, Ordering::SeqCst);
}
```

Wait-free data structures tend to be very complicated to implement. They are used when you need the strongest possible progress guarantee.

## Prerequisites

- [[lock-free-data-structures]] — Wait-free is a stronger guarantee than lock-free
- [[atomic-operations]] — Wait-free structures rely on bounded atomic operations like fetch_add

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[lock-free-data-structures]]
- [[non-blocking-data-structures]]
- [[atomic-operations]]
