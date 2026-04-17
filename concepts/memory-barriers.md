---
tags:
  - concept
  - ece459
  - memory-consistency
  - synchronization
lectures:
  - L15
prerequisites:
  - "[[compiler-reordering]]"
  - "[[hardware-reordering]]"
  - "[[out-of-order-execution]]"
---

# Memory Barriers

A memory barrier (also called a fence) is a hardware or compiler instruction that prevents reordering of memory operations across the barrier. It ensures that all memory accesses before the barrier become visible to the system before any accesses after the barrier take effect. Memory barriers are the primary tool for establishing ordering guarantees in concurrent programs.

The x86 architecture defines three types of memory barriers: `mfence` (all loads and stores before become visible before any loads and stores after), `sfence` (all stores before become visible before all stores after), and `lfence` (all loads before become visible before all loads after). Note that an `sfence` on one CPU makes stores visible, but another CPU must execute an `lfence` or `mfence` to read those stores in the correct order.

Memory fences are costly. They prevent reorderings that would otherwise speed up execution, and they can force a thread to wait for another. [[sequential-consistency]] necessarily generates memory fences to produce correct results. Weaker orderings like [[acquire-release-ordering]] use fewer or cheaper barriers, which is why they can offer better performance when correctness can be proven. In practice, programmers rarely insert barriers directly -- instead they use atomic operations with the appropriate [[memory-consistency-models]] ordering, and the compiler emits the necessary barriers.

## Prerequisites

- [[compiler-reordering]] — Memory barriers prevent unsafe compiler reorderings
- [[hardware-reordering]] — Memory barriers prevent unsafe hardware reorderings
- [[out-of-order-execution]] — Understanding why CPUs reorder instructions in the first place

## Lectures

- [[L15-Memory-Consistency]]

## Related Concepts

- [[compiler-reordering]]
- [[hardware-reordering]]
- [[sequential-consistency]]
- [[memory-consistency-models]]
- [[atomic-operations]]
