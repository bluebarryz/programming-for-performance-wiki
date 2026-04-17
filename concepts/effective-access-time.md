---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[memory-hierarchy]]"
  - "[[cache-misses]]"
---

# Effective Access Time

The effective access time formula quantifies the average time to access data given cache hit ratios. For a single level of cache:

```
Effective Access Time = h * t_c + (1 - h) * t_m
```

Where `h` is the hit ratio, `t_c` is cache access time, and `t_m` is main memory access time.

For virtual memory (where `p` is the probability the page is in memory and `t_d` is disk access time):

```
Effective Access Time = p * t_m + (1 - p) * t_d
```

The combined formula for a system with one level of cache and virtual memory:

```
Effective Access Time = h * t_c + (1 - h)(p * t_m + (1 - p) * t_d)
```

The disk read term `t_d` dominates because it is orders of magnitude larger than memory access time. With memory at ~200 ns and disk at ~8 ms, the access time in nanoseconds is roughly `(1 - p) * 8,000,000`. This is why the page fault rate must be extremely low for reasonable performance.

The formula extends to multilevel caches (L1, L2, L3) with different access times and hit rates at each level.

## Prerequisites

- [[memory-hierarchy]] — The formula models access time across multiple hierarchy levels
- [[cache-misses]] — The hit/miss ratio is the key variable in the formula

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[cache-misses]]
- [[memory-hierarchy]]
- [[cpu-memory-gap]]
