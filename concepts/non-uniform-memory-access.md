---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[multicore-processors]]"
  - "[[memory-hierarchy]]"
---

# Non-Uniform Memory Access

In Non-Uniform Memory Access (NUMA) systems, different CPUs can access different resources at different speeds (not just memory -- resources in general). Each CPU has its own memory bank, and accessing local memory is faster than accessing another CPU's memory.

This contrasts with [[symmetric-multiprocessing]], where all CPUs have approximately the same access time. In NUMA, the operating system should schedule tasks on the CPUs that can access the needed resources fastest. Since memory is commonly the bottleneck, placing threads near their data is important.

NUMA awareness matters for performance: the OS scheduler must account for which memory bank holds the data a thread needs. Poor NUMA placement can significantly increase memory access latency.

## Prerequisites

- [[multicore-processors]] — NUMA arises in systems with multiple processor sockets or chiplets
- [[memory-hierarchy]] — NUMA extends the hierarchy concept with non-uniform access latencies across sockets

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[symmetric-multiprocessing]]
- [[multicore-processors]]
- [[memory-hierarchy]]
