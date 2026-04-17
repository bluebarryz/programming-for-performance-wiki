---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[multicore-processors]]"
---

# Symmetric Multiprocessing

In a Symmetric Multiprocessing (SMP) system, all CPUs have approximately the same access time for resources (subject to cache misses). The cores are mostly alike in design and capability. This is the most common multicore design.

The SMP design where cores share a cache is especially good for the 1:1 threading model -- the design of the cores doesn't need to change much, but they still need to communicate with each other and the rest of the system.

Contrast with [[non-uniform-memory-access]], where CPUs can access different resources at different speeds. Also contrast with non-SMP systems like the Cell processor (with a PowerPC main core and 7 Synergistic Processing Elements) or modern Intel/AMD chips with heterogeneous core types.

Solaris "processor sets" and Linux "affinity" are OS features for controlling which virtual CPUs run which processes, helping reduce task switches and resource contention in SMP systems.

## Prerequisites

- [[multicore-processors]] — SMP is a design model for how multiple cores share resources

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[multicore-processors]]
- [[hyperthreading]]
- [[non-uniform-memory-access]]
