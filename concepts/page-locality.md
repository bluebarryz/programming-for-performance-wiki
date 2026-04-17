---
tags:
  - concept
  - ece459
  - pogo
  - cache
  - optimization
lectures:
  - L27
prerequisites:
  - "[[memory-hierarchy]]"
  - "[[cache-misses]]"
  - "[[profile-guided-optimization]]"
---

# Page Locality

Page locality refers to the goal of placing related code close together in the binary so that frequently called functions reside on the same memory page. When a called function is on the same page as the caller, it avoids a cache miss or page fault.

[[profile-guided-optimization|POGO]] uses call graph profiling data to reorder code blocks in the binary. The most common execution paths are packed together, and subsequent steps are placed adjacent to each other. Cold or dead code is moved to separate sections to avoid polluting hot pages.

In POGO benchmark results, page locality ranged from 75% to 98% across different programs, contributing significantly to the observed speed gains.

## Prerequisites

- [[memory-hierarchy]] — Page locality exploits the memory hierarchy to avoid cache misses and page faults
- [[cache-misses]] — The goal of page locality is reducing cache misses by co-locating related code
- [[profile-guided-optimization]] — POGO uses profiling data to reorder code for better page locality

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[pogo-optimizations]]
- [[hot-and-cold-code]]
- [[profile-guided-optimization]]
