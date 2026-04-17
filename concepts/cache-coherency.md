---
tags:
  - concept
  - ece459
  - cache
  - hardware
lectures:
  - "08"
prerequisites:
  - "[[memory-hierarchy]]"
  - "[[multicore-processors]]"
  - "[[cache-misses]]"
---

# Cache Coherency

Cache coherency is the problem of keeping data consistent across multiple CPU caches. In a multicore system, each CPU typically has its own L1/L2 cache. If CPU 1 reads a value and CPU 3 later modifies it, CPU 1's cached copy becomes stale. Cache coherency protocols ensure two properties: (1) the values in all caches are consistent, and (2) the system behaves as if all CPUs share a single memory.

The simplest (and worst) solution is to declare variables as non-cacheable, forcing all reads from main memory. This destroys cache hit ratios and performance. Instead, hardware implements coherency protocols that allow caches to remain useful while staying in sync. The two fundamental actions when a change is detected are invalidation (marking the stale copy as invalid, requiring a fresh fetch on next access) and update (pushing the new value to all caches immediately). Invalidation is more common because it uses less bandwidth.

These same principles apply beyond hardware. Software distributed caches like Redis use analogous strategies -- the difference is that in software you may get to choose the configuration, whereas with CPU hardware you get whatever the chip designers provided. The protocols discussed in the course (MSI, MESI, MESIF) provide progressively more efficient ways to manage coherency with minimal bus traffic.

## Prerequisites

- [[memory-hierarchy]] — Cache coherency arises because each core has its own L1/L2 cache in the hierarchy
- [[multicore-processors]] — The problem only exists when multiple cores each have private caches
- [[cache-misses]] — Stale cached data from coherency failures manifests as incorrect cache hits

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[snoopy-caches]]
- [[msi-protocol]]
- [[mesi-protocol]]
- [[mesif-protocol]]
- [[false-sharing]]
- [[write-through-cache]]
- [[write-back-cache]]
- [[invalidation-vs-update]]
