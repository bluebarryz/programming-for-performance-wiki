---
tags:
  - concept
  - ece459
  - L12
  - concurrency
  - lock-freedom
prerequisites:
  - "[[data-races]]"
  - "[[locking-and-synchronization]]"
---

# Atomic Operations

Atomic operations are indivisible operations supported by hardware (e.g., test-and-set, [[compare-and-swap]]). Other threads see the state either before or after the operation -- never an intermediate state. They are a lower-overhead alternative to locks for suitable operations.

In Rust, atomic types exist for integers (signed/unsigned), booleans, size types, and pointers (e.g., `AtomicBool`, `AtomicI32`, `AtomicPtr`). Values must be accessed through `load()` and `store()` methods with an explicit memory ordering parameter. Additional operations include:

- `fetch_add`, `fetch_sub` -- atomic arithmetic
- `fetch_max`, `fetch_min` -- atomic min/max
- `and`, `nand`, `or`, `xor` -- atomic bitwise operations
- `compare_and_swap`, `compare_exchange` -- [[compare-and-swap]]

Caveats:
- Atomics ensure individual operations are indivisible but do not prevent race conditions if threads aren't properly coordinated.
- Not all atomic types are portable across all platforms; emulation or larger types may be used.

## Prerequisites

- [[data-races]] — Atomics solve the problem of concurrent unsynchronized access
- [[locking-and-synchronization]] — Atomics are a lower-overhead alternative to locks

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[compare-and-swap]]
- [[spinlock]]
- [[lock-free-data-structures]]
- [[sequential-consistency]]
- [[memory-consistency-models]]
