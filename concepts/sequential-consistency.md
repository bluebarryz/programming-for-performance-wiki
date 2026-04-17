---
tags:
  - concept
  - ece459
  - memory-consistency
  - atomics
lectures:
  - L15
prerequisites:
  - "[[atomic-operations]]"
  - "[[compiler-reordering]]"
  - "[[hardware-reordering]]"
---

# Sequential Consistency

Sequential consistency is the strongest memory ordering model. As defined by Leslie Lamport: "the result of any execution is the same as if the operations of all the processors were executed in some sequential order, and the operations of each individual processor appear in this sequence in the order specified by its program." In other words, there exists a single global ordering of all operations that every thread agrees on, and that ordering is consistent with each thread's program order.

In a sequentially consistent system, given two threads where T1 does `x = 1; r1 = y` and T2 does `y = 1; r2 = x` (with x and y initially 0), we would always observe a state consistent with some interleaving of these operations. The outcome where both r1 and r2 remain 0 is impossible under sequential consistency, because that would require both reads to happen before both writes, which contradicts program order.

Sequential consistency is expensive to implement because it requires [[memory-barriers]] on every atomic operation to prevent both [[compiler-reordering]] and [[hardware-reordering]]. Most real systems implement weaker models by default. In Rust and C++, `Ordering::SeqCst` provides sequential consistency and is the recommended default for atomic operations because it is the easiest to reason about correctly. Weaker orderings like [[acquire-release-ordering]] and [[relaxed-ordering]] offer better performance but are much harder to use correctly.

## Prerequisites

- [[atomic-operations]] — Sequential consistency is a memory ordering for atomic operations
- [[compiler-reordering]] — SeqCst prevents compiler reordering across atomic accesses
- [[hardware-reordering]] — SeqCst prevents hardware reordering via memory barriers

## Lectures

- [[L15-Memory-Consistency]]

## Related Concepts

- [[memory-consistency-models]]
- [[memory-barriers]]
- [[acquire-release-ordering]]
- [[relaxed-ordering]]
- [[compiler-reordering]]
- [[hardware-reordering]]
- [[atomic-operations]]
