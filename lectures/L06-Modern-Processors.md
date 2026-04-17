---
tags:
  - lecture
  - ece459
  - hardware
  - processors
  - performance
lecture: 6
title: Modern Processors
date: 2024-09-09
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
---

# L06 - Modern Processors

Understanding hardware is critical for writing performant programs. This lecture, based on Cliff Click's talk, covers why CPU clock speeds plateaued around 2005 at ~3 GHz due to power/heat limits, and how modern processors use instruction-level parallelism (ILP) techniques to squeeze more work out of each cycle. It also examines the growing CPU-memory speed gap and the importance of cache hit ratios.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Pipelining concepts and the performance fundamentals this lecture deepens at the hardware level

## Concepts Covered

- [[von-neumann-architecture]]
- [[frequency-scaling]]
- [[cisc-vs-risc]]
- [[pipelining]]
- [[pipeline-hazards]]
- [[instruction-level-parallelism]]
- [[out-of-order-execution]]
- [[register-renaming]]
- [[speculation]]
- [[branch-prediction]]
- [[dual-issue]]
- [[miss-shadow]]
- [[cache-misses]]
- [[effective-access-time]]
- [[memory-hierarchy]]
- [[sram-vs-dram]]
- [[cpu-memory-gap]]
