---
tags:
  - concept
  - ece459
  - cache
  - hardware
lectures:
  - "08"
prerequisites:
  - "[[write-back-cache]]"
  - "[[snoopy-caches]]"
  - "[[invalidation-vs-update]]"
---

# MSI Protocol

MSI is the simplest write-back cache coherency protocol, using three states: Modified, Shared, and Invalid. Modified means only this cache has a valid copy and main memory is out-of-date. Shared means the location is unmodified, up-to-date with main memory, and may exist in other caches. Invalid means the cached copy is not valid.

The protocol uses two bus operations beyond normal reads: BusWB (write-back/flush, which writes modified data back to memory) and BusRdX (exclusive read, which signals intent to write). When a processor writes to a Shared line, it issues a BusRdX, which causes all other caches holding that line to invalidate their copies. The writing cache then transitions to Modified. When another processor later reads the line, the Modified cache writes back the data (BusWB), both caches transition to Shared, and the data is now consistent.

Compared to [[write-through-cache]], MSI delays writes to main memory as long as possible, which is beneficial when a processor writes to the same location multiple times in succession. Instead of flushing to memory on every write, the data stays in cache and is only written back when another processor needs it. This is the foundation for more advanced protocols like [[mesi-protocol]] and [[mesif-protocol]].

## Prerequisites

- [[write-back-cache]] — MSI is the simplest write-back coherency protocol
- [[snoopy-caches]] — MSI relies on bus snooping to detect reads and writes from other caches
- [[invalidation-vs-update]] — MSI uses the invalidation approach when another cache writes

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[cache-coherency]]
- [[write-back-cache]]
- [[mesi-protocol]]
- [[snoopy-caches]]
