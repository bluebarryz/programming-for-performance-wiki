---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[frequency-scaling]]"
  - "[[memory-hierarchy]]"
  - "[[sram-vs-dram]]"
---

# CPU-Memory Gap

The speed of memory has not kept up with CPU advances. CPU frequency doubled approximately every 2 years, while DRAM speed doubled approximately every 6 years. This growing gap means that runtime has shifted from being dominated by page faults (in the disk era) to being dominated by cache misses (in the memory era).

Adding more cache helps but is not a perfect solution -- doubling a cache level (at great expense) may only speed up the program by a small amount. This is one of the "four walls" limiting processor performance, alongside the power wall, ILP limits, and the speed of light.

In the SSD era, "disk" reads are about as fast as memory reads, making memory the new bottleneck. As the course puts it: "memory is the new disk."

## Prerequisites

- [[frequency-scaling]] — The gap exists because CPU frequency grew faster than memory speed
- [[memory-hierarchy]] — Caches exist to bridge the CPU-memory gap
- [[sram-vs-dram]] — The gap is between fast SRAM caches and slow DRAM main memory

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[memory-hierarchy]]
- [[sram-vs-dram]]
- [[cache-misses]]
- [[effective-access-time]]
