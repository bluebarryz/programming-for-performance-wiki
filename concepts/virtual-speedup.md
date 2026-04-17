---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "28"
prerequisites:
  - "[[causal-profiling]]"
---

# Virtual Speedup

Virtual speedup is the key technique underlying [[causal-profiling]]. It is based on the observation that speeding up one area of code is fundamentally equivalent to slowing down every other area of code. By adding pauses to other threads, a profiler can simulate the effect of optimizing a target function without actually changing any code.

Concretely, to simulate speeding up function f by a factor d (e.g., 40%), the profiler pauses all other threads for a duration of d multiplied by the execution time of f. The original program runtime, the hypothetical speedup from actually optimizing f, and the virtual speedup from pausing other threads all produce equivalent relative timing relationships between threads. This equivalence is what makes the technique valid.

The [[coz-profiler]] uses virtual speedup to test various optimization percentages for each code region and measure the resulting impact on overall program throughput or latency. [[Scoz]] extends this to a core-based approach, pausing execution on all other cores rather than just other threads, which allows it to account for kernel and multi-process effects. Virtual speedup introduces overhead (about 10% of Coz's total 17.6% overhead) from the delays injected into other threads.

## Prerequisites

- [[causal-profiling]] — Virtual speedup is the core mechanism that makes causal profiling work

## Lectures
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts
- [[causal-profiling]]
- [[coz-profiler]]
- [[scoz]]
- [[critical-path]]
