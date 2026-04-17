---
tags:
  - concept
  - ece459
  - hardware
  - performance
  - L06
prerequisites:
  - "[[memory-hierarchy]]"
  - "[[caching]]"
---

# Cache Misses

A cache miss occurs when the CPU requests data that is not found in the cache, requiring a slower fetch from a lower level of the [[memory-hierarchy]]. A cache hit is when the data is found in the cache.

The hit ratio is the percentage of accesses that are cache hits. Even small miss rates dominate performance. Cliff Click noted that 5% miss rates dominate performance. Using SPEC CPU2006 benchmark data with L1D miss rate of 40 permil and L2 miss rate of 4 permil, assuming L1D miss penalty of 5 cycles and L2 miss penalty of 300 cycles, the average cycles per instruction becomes:

```
1 + 0.04 * 5 + 0.004 * 300 = 2.4
```

This means cache misses more than double the effective CPI. As the course emphasizes: "misses are not just expensive, they hurt performance more than anything else."

According to the lecture, 90-99% of transistors on a modern x86 chip are spent on cache, because preventing the performance hit of going to memory is so important.

## Prerequisites

- [[memory-hierarchy]] — Cache misses are defined by which level of the hierarchy the data is found in
- [[caching]] — Understanding caching as a general performance strategy from L01

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[effective-access-time]]
- [[memory-hierarchy]]
- [[miss-shadow]]
- [[cpu-memory-gap]]
- [[cache-coherency]]
