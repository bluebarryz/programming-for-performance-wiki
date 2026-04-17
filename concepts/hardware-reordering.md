---
tags:
  - concept
  - ece459
  - memory-consistency
  - reordering
lectures:
  - L15
prerequisites:
  - "[[out-of-order-execution]]"
  - "[[pipelining]]"
  - "[[cache-coherency]]"
---

# Hardware Reordering

Hardware reordering is the CPU's ability to execute a sequence of instructions in a different order than they were issued, independent of any compiler optimizations. The CPU receives instructions and may choose to execute them in whatever order it finds more efficient, for example to hide memory latency or keep execution units busy.

A key concern with hardware reordering in concurrent programs is visibility of updates from other threads. When thread A checks a variable that thread B has written, hardware reordering might cause thread A's read to be reordered relative to thread B's write, producing stale or "wrong" results. This goes beyond single-thread data dependencies -- the CPU respects those -- but cross-thread ordering is not guaranteed without explicit [[memory-barriers]].

Different architectures provide different guarantees. Old x86 (386) CPUs did no reordering at all. Modern x86 provides relatively strong ordering with only a few specific violations. ARM, which is increasingly popular, has weak ordering and will freely reorder instructions except where there are data dependencies. This means code that works correctly on x86 may break on ARM without proper memory ordering annotations. The solution is to use atomic operations with appropriate [[memory-consistency-models]] rather than relying on architecture-specific behaviour.

## Prerequisites

- [[out-of-order-execution]] — Hardware reordering is the CPU executing instructions out of order
- [[pipelining]] — Understanding why the CPU reorders instructions to keep the pipeline busy
- [[cache-coherency]] — Cross-thread visibility of writes depends on cache coherency protocols

## Lectures

- [[L15-Memory-Consistency]]

## Related Concepts

- [[compiler-reordering]]
- [[memory-barriers]]
- [[sequential-consistency]]
- [[memory-consistency-models]]
