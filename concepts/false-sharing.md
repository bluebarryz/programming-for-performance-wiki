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
  - "[[cache-misses]]"
---

# False Sharing

False sharing occurs when two unrelated data elements happen to reside on the same cache line. When one thread writes to its element, the cache coherency protocol invalidates the entire cache line, forcing any other CPU working on the other element to re-fetch it from memory. This creates unnecessary cache misses and bus traffic even though the data is logically independent.

A classic example involves two adjacent arrays `char a[10]` and `char b[10]`. Since they are allocated consecutively in memory, they almost certainly share a cache line. If one thread writes to `a` while another reads `b`, the writes to `a` will repeatedly invalidate `b` in the other CPU's cache. Experiments show that increasing the byte separation between the arrays to ensure they land on different cache lines can yield a 5x speedup.

The fix for false sharing is to ensure that data accessed by different threads does not share a cache line. Techniques include heap-allocating arrays separately (though this is not guaranteed to separate them), padding data structures to be at least one cache line apart, or using compiler/language features to control alignment. The cost is wasted space, but the performance gain is substantial enough to justify it.

## Prerequisites

- [[cache-coherency]] — False sharing is caused by coherency protocols invalidating entire cache lines
- [[cache-misses]] — False sharing creates unnecessary cache misses between cores

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[cache-coherency]]
- [[mesi-protocol]]
- [[cache-misses]]
