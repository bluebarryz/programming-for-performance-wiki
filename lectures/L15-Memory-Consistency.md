---
tags:
  - lecture
  - ece459
  - memory-consistency
  - memory-barriers
  - reordering
lecture: L15
title: "Memory Consistency"
prerequisite_lectures:
  - "[[L06-Modern-Processors]]"
  - "[[L08-Cache-Coherency]]"
  - "[[L12-Lock-Convoys-Atomics-Lock-Freedom]]"
---

# L15 -- Memory Consistency

This lecture explains why memory ordering matters for concurrent programs. Both compilers and hardware can reorder instructions for performance, which can break assumptions in multithreaded code. Sequential consistency is the intuitive model (operations appear to execute in program order across all threads) but is expensive. The lecture covers x86 memory barriers (mfence, sfence, lfence), the Rust/C++ memory consistency models, and the Acquire-Release and Relaxed orderings as alternatives to sequential consistency. A real-world bug in the crossbeam crate illustrates the dangers of incorrect memory ordering.

## Prerequisite Lectures
- [[L06-Modern-Processors]] — Out-of-order execution concepts needed to understand hardware reordering
- [[L08-Cache-Coherency]] — Cache coherence protocols needed to understand memory visibility between cores
- [[L12-Lock-Convoys-Atomics-Lock-Freedom]] — Atomic operations needed as the foundation for memory ordering semantics

## Concepts Covered

- [[compiler-reordering]]
- [[hardware-reordering]]
- [[sequential-consistency]]
- [[memory-barriers]]
- [[acquire-release-ordering]]
- [[relaxed-ordering]]
- [[memory-consistency-models]]
