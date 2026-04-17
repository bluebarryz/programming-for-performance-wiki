---
tags:
  - concept
  - ece459
  - memory
  - diagnostics
lectures:
  - L26
prerequisites:
  - "[[bottleneck-analysis]]"
  - "[[memory-hierarchy]]"
---

# Memory Bottleneck Diagnosis

Memory appearing "full" in `top` is not necessarily a problem -- the OS uses available RAM for caching and there is no benefit to keeping memory free. The real indicator of a memory bottleneck is **swapping**: when the system runs out of physical RAM and starts paging to disk, performance collapses.

In garbage-collected languages, excessive or long GC pauses, or out-of-memory crashes, are signs of memory pressure.

You can check page faults with `ps -eo min_flt,maj_flt,cmd` (major faults = fetched from disk, minor faults = copied from another process), but this is a lifetime count and not very useful on its own.

## Prerequisites

- [[bottleneck-analysis]] — Memory diagnosis is one step in systematic bottleneck analysis
- [[memory-hierarchy]] — Understanding cache and RAM levels explains why swapping is so costly

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[bottleneck-analysis]]
- [[swap-and-paging]]
