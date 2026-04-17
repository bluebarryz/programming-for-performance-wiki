---
tags:
  - concept
  - ece459
  - cache
  - hardware
lectures:
  - "08"
prerequisites:
  - "[[cache-coherency]]"
  - "[[snoopy-caches]]"
---

# Write-Through Cache

Write-through caching is the simplest cache coherency strategy. All cache writes are immediately propagated to main memory, and all writes appear on the shared bus. Other CPUs snoop the bus and, if they hold the same memory location in their cache, either invalidate or update their copy.

The protocol uses two states per cached location: Valid and Invalid. When a processor writes (PrWr), a BusWr is generated and the data goes to memory, keeping the local copy valid. Other caches observing the BusWr mark their copy as Invalid. When a processor reads from an Invalid location (PrRd), a BusRd is generated to fetch the current value from memory.

Write-through's main advantage is simplicity: main memory always has the most recent value, so any cache miss can be serviced directly from memory. The disadvantage is performance -- if a CPU writes to the same location repeatedly, every write goes to memory even if no other processor needs the data. This motivated the development of [[write-back-cache]] protocols like [[msi-protocol]], which delay memory writes until another processor actually requests the data. Write-through also supports the less common write broadcast approach, where all caches are updated on every write. This prevents the cache miss following an invalidation but uses significantly more bandwidth.

## Prerequisites

- [[cache-coherency]] — Write-through is the simplest coherency strategy
- [[snoopy-caches]] — Write-through relies on snooping the bus to detect writes

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[write-back-cache]]
- [[cache-coherency]]
- [[snoopy-caches]]
- [[invalidation-vs-update]]
