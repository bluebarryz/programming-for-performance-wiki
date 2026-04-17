---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[frequency-scaling]]"
---

# Multicore Processors

Multicore processors exist because clock speeds stopped increasing due to the power wall. Each processor core executes instructions independently, so a processor with multiple cores can simultaneously execute multiple unrelated instructions.

**Chips vs Cores**: A multiprocessor (SMP) system has multiple physical CPUs on the board. A multicore chip has multiple cores on a single die that look like distinct CPUs to the operating system. You can count chips by looking at the board; cores are harder to count -- the chip exposes "virtual CPUs" and the OS schedules work on them.

Hardware designs for multicores vary:
- **SMP design**: Cores share a cache, good for the 1:1 threading model
- **Hyperthreading (N:1)**: Multiple hardware threads share one core
- **M:N model**: Many cores, each with multiple hardware threads (e.g., AMD Ryzen 5 7600 has 6 cores, 12 threads)

Modern chips also have heterogeneous cores: Intel has P (performance) and E (efficient) cores; AMD has c-cores. P cores are for low-latency work, E cores trade latency for density.

## Prerequisites

- [[frequency-scaling]] — Multicore exists because clock speeds hit a wall due to the power wall

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[frequency-scaling]]
- [[symmetric-multiprocessing]]
- [[hyperthreading]]
- [[non-uniform-memory-access]]
- [[cache-coherency]]
