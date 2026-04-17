---
tags:
  - concept
  - ece459
  - L13
  - concurrency
  - speculation
prerequisites:
  - "[[locking-and-synchronization]]"
  - "[[deadlock]]"
  - "[[data-races]]"
---

# Software Transactional Memory

Software transactional memory (STM) applies groups of changes speculatively, assuming they will succeed, and checks afterwards for conflicts. If a conflict is detected, the transaction is rolled back and retried.

The programming model resembles database transactions: wrap operations in an `atomically` block, and the runtime ensures they either all succeed or are rolled back:
```rust
let x = atomically(|trans| {
    var.write(trans, 42)?;
    var.read(trans)
});
```

Benefits:
- Much simpler programming model than locks -- no need to remember lock ordering or worry about deadlocks

Drawbacks:
- **I/O**: Side effects like writes to screen or network cannot be rolled back
- **Nested transactions**: Committing an inner transaction while aborting the outer one is problematic
- **Transaction size**: Hardware implementations may have size limits

Implementations are typically optimistic, buffering changes and rolling back if necessary. Hardware support (using caches) can help but has size limits.

Important caveat: atomic blocks don't prevent data races -- intermediate states may still be visible to other threads during execution, even though the final result is atomic.

## Prerequisites

- [[locking-and-synchronization]] — STM is an alternative to lock-based synchronization
- [[deadlock]] — STM eliminates the deadlock problems of lock-based approaches
- [[data-races]] — Understanding the concurrent access problems STM addresses

## Lectures

- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[speculative-execution]]
- [[deadlock]]
- [[side-effects]]
