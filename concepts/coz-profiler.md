---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "28"
prerequisites:
  - "[[causal-profiling]]"
  - "[[virtual-speedup]]"
---

# Coz Profiler

Coz (pronounced like "cause") is a causal profiler created by Charlie Curtsinger and Emery Berger. It performs what-if analysis to determine the impact of speeding up a particular part of a program, without requiring any code changes. Rather than simply reporting where time is spent, Coz predicts which optimizations would actually improve end-to-end performance.

Coz works by applying [[virtual-speedup]]: instead of actually making a target function faster, it pauses all other threads for a proportional duration, producing an equivalent effect. The profiler generates graphs showing potential program speedup for each code region at various optimization levels, revealing whether optimization would yield linear improvement, capped improvement, no effect, or even negative impact due to effects like increased lock contention.

The overhead of Coz is estimated at 17.6%, broken down into 2.6% for startup debug information collection, 4.8% for sampling, and 10.2% for the delays introduced by virtual speedups. The authors demonstrated meaningful speedups (up to 68%) on real applications including Memcached, SQLite, and others, often requiring very few lines of code changes. A limitation of Coz is that it operates on threads within a single machine and would need significant extension to work for distributed systems.

## Prerequisites

- [[causal-profiling]] — Coz is the primary implementation of causal profiling
- [[virtual-speedup]] — Coz uses virtual speedup as its core measurement technique

## Lectures
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts
- [[causal-profiling]]
- [[virtual-speedup]]
- [[scoz]]
- [[profiling]]
