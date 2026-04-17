---
tags:
  - concept
  - ece459
  - memory-consistency
  - concurrency
lectures:
  - L15
prerequisites:
  - "[[atomic-operations]]"
  - "[[compiler-reordering]]"
  - "[[hardware-reordering]]"
  - "[[cache-coherency]]"
---

# Memory Consistency Models

A memory consistency model defines the rules for how memory operations (reads and writes) from different threads become visible to each other. Rust adopts the C++ memory model, not because it is easy to understand, but because it is the best available attempt at formally modelling atomic operations -- a notoriously difficult subject.

The purpose of the memory model is to reason about causality: establishing "happens-before" relationships between events such as "event A happens before event B." The strongest model is [[sequential-consistency]], where all threads observe operations in a single global order consistent with each thread's program order. This is the easiest to reason about but the most expensive to implement because it requires [[memory-barriers]] on every atomic operation.

Weaker models trade ease of reasoning for performance. [[acquire-release-ordering]] establishes happens-before only between specific pairs of acquire and release operations, which is cheaper on weakly-ordered hardware like ARM. [[relaxed-ordering]] provides no ordering guarantees at all, allowing all reorderings; it is suitable only for operations like simple counters where ordering does not matter. A real-world bug in the `crossbeam` crate demonstrated the danger of getting ordering wrong: incorrect use of relaxed ordering caused an assertion failure due to garbage register values, and the bug was invisible in debug mode because the debugger prevented the reordering.

## Prerequisites

- [[atomic-operations]] — Memory models define ordering semantics for atomic operations
- [[compiler-reordering]] — Memory models constrain what the compiler may reorder
- [[hardware-reordering]] — Memory models constrain what the hardware may reorder
- [[cache-coherency]] — Cache coherency determines how writes become visible across cores

## Lectures

- [[L15-Memory-Consistency]]

## Related Concepts

- [[sequential-consistency]]
- [[acquire-release-ordering]]
- [[relaxed-ordering]]
- [[memory-barriers]]
- [[compiler-reordering]]
- [[hardware-reordering]]
- [[atomic-operations]]
