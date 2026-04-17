---
tags:
  - concept
  - ece459
  - cache
  - hardware
lectures:
  - "08"
prerequisites:
  - "[[write-through-cache]]"
  - "[[cache-coherency]]"
---

# Write-Back Cache

Write-back caching is a strategy that delays writing modified data to main memory as long as possible, only flushing when another processor needs the data. This improves performance over [[write-through-cache]] by avoiding redundant memory writes. If a CPU writes to the same location three times in rapid succession, a write-through cache would flush to memory three times, while a write-back cache does it only once (or not at all, if no other processor requests the data).

The implementation requires hardware support for a "dirty" bit that indicates the cached data has been modified but not yet written to memory. The simplest write-back protocol is [[msi-protocol]], which uses three states (Modified, Shared, Invalid). When a cache line is in the Modified state, the data exists only in that cache and main memory is stale. If another processor reads the same address, the modified cache writes back the data (BusWB), both copies become Shared, and memory is updated.

Write-back caching is the foundation for the [[mesi-protocol]] and [[mesif-protocol]], which add further states to reduce unnecessary bus traffic. The same principle applies in software distributed caches, where dirty items are written to the database only when necessary -- such as when another node requests the data or when the owning node shuts down.

## Prerequisites

- [[write-through-cache]] — Write-back improves on write-through by delaying memory writes
- [[cache-coherency]] — Write-back requires more sophisticated coherency protocols

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[write-through-cache]]
- [[msi-protocol]]
- [[mesi-protocol]]
- [[cache-coherency]]
- [[distributed-cache-software]]
