---
tags:
  - concept
  - ece459
  - memory
  - diagnostics
lectures:
  - L26
prerequisites:
  - "[[memory-hierarchy]]"
  - "[[bottleneck-analysis]]"
---

# Swap and Paging

The key tool for diagnosing memory-related slowdowns is `vmstat`, which reports swap-in (`si`) and swap-out (`so`) rates over time. If both are consistently zero, memory is not the bottleneck. Significant swapping activity indicates the system is running out of physical RAM and resorting to disk-backed virtual memory, which destroys performance and scalability.

A small amount of swapping may be inevitable, but heavy swapping is a critical problem requiring either more RAM or reduced memory usage.

## Prerequisites

- [[memory-hierarchy]] — Swapping involves moving data between RAM and disk, the slowest level of the hierarchy
- [[bottleneck-analysis]] — Swap diagnosis is part of the systematic bottleneck identification process

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[memory-bottleneck-diagnosis]]
- [[bottleneck-analysis]]
- [[disk-bottleneck-diagnosis]]
