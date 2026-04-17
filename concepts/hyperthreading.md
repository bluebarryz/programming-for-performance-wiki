---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[multicore-processors]]"
  - "[[pipelining]]"
---

# Hyperthreading

Hyperthreading (also called Simultaneous Multithreading, SMT) allows multiple hardware threads to share a single physical core. The CPU exposes these as virtual CPUs to the operating system.

In the N:1 model, two threads share one core. Whether this helps depends on the instruction mix: if both threads compete for the same resource (e.g., ALUs), each runs more slowly. If they do different things, there is potential for speedup.

In the M:N model, multiple cores each have multiple threads. For example, the AMD Ryzen 5 7600 (Zen 4) has 6 cores and 12 threads -- each core has its own L1 and L2 caches, while L3 is shared among cores on the same "Core Complex Die."

Two threads on the same core will generally run more slowly than two threads on separate cores due to resource contention. Task switches between cores are also slow because they may require reloading caches.

Hyperthreading is also a security concern: since two threads share the same execution core and hardware, one thread can observe the other's behavior through timing side-channels. See [[side-channel-attacks]].

## Prerequisites

- [[multicore-processors]] — Hyperthreading is a technique for sharing a single core among multiple hardware threads
- [[pipelining]] — Understanding the pipeline is needed to see how threads share execution resources

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[multicore-processors]]
- [[symmetric-multiprocessing]]
- [[side-channel-attacks]]
