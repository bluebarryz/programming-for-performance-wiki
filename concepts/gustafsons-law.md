---
tags:
  - concept
  - ece459
  - parallelism
lectures:
  - "09"
prerequisites:
  - "[[amdahls-law]]"
  - "[[parallelism]]"
---

# Gustafson's Law

Gustafson's Law, proposed in 1988, offers a more optimistic view of parallel computing than [[amdahls-law]]. While Amdahl assumes a fixed problem size (asking "how fast can we solve this problem?"), Gustafson observes that in practice the point of more processors is to solve bigger problems. The question becomes: "how big a problem can we solve in a fixed amount of time?"

The key insight is that as you scale up the problem size -- more data, finer grid resolution, more timesteps -- the amount of parallel work tends to increase while the serial portion remains roughly constant. As long as the algorithm scales linearly, it is possible to handle linearly larger problems with a linearly larger number of processors. This is why, despite Amdahl's pessimism, multicore computers are ubiquitous.

Gustafson's Law works best when there is a "problem-size knob" that can be turned up. Google is a practical example: their systems deal with massive datasets where the parallel portion vastly dominates the serial overhead. For problems where the size is truly fixed and cannot grow, Amdahl's Law still applies and the serial fraction remains the binding constraint on speedup.

## Prerequisites

- [[amdahls-law]] — Gustafson's Law is a response to Amdahl's pessimistic fixed-size assumption
- [[parallelism]] — Understanding parallel speedup is needed for the law's argument

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]

## Related Concepts
- [[amdahls-law]]
- [[concurrency-vs-parallelism]]
- [[parallelization-overhead]]
