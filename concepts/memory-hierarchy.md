---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[caching]]"
---

# Memory Hierarchy

Modern processors use a hierarchy of memory levels with different speeds and sizes:

- **L1 cache** -- Smallest, fastest (a few cycles). Unique to each core.
- **L2 cache** -- Larger, slower. Often per-core.
- **L3 cache** -- Largest on-chip cache, shared across cores. Not much faster than main memory in some designs, but this is where [[cache-coherency]] communication often happens.
- **Main memory (DRAM)** -- Much slower (200-300 cycles).
- **Disk/SSD** -- Orders of magnitude slower.

If data is not in L1, the CPU checks L2, then L3, then main memory. Each miss cascades to the next level. Intel 64-bit CPUs typically have L1, L2, and L3 caches.

The [[effective-access-time]] formula accounts for these multiple levels. In the era of SSDs, memory reads have become the rate-limiting step (rather than disk), making the CPU-memory gap the dominant performance concern.

## Prerequisites

- [[caching]] — The memory hierarchy is a hardware implementation of the caching principle from L01

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[cache-misses]]
- [[effective-access-time]]
- [[sram-vs-dram]]
- [[cpu-memory-gap]]
