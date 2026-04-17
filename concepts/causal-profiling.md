---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "28"
prerequisites:
  - "[[cpu-profiling]]"
  - "[[improving-latency]]"
  - "[[sampling-vs-instrumentation-profiling]]"
---

# Causal Profiling

Causal profiling is a technique for determining which parts of a program would yield the most benefit if optimized, without actually changing any code. It answers the question: "what would be the impact of speeding up this particular part of the code?" This is valuable because traditional profiling tells you where time is spent, but not whether optimizing that code would improve overall performance.

The key insight is that speeding up one area of code is equivalent to slowing down every other part of the code. This is called a [[virtual-speedup]]. To simulate speeding up a function f by a factor d, the profiler pauses all other threads for a duration proportional to d times the execution time of f. This produces the same relative effect as actually making f faster. The tool then measures the impact on overall program runtime across various simulated speedup percentages.

The results can show several outcomes: continuous linear speedup (optimizing this code always helps), speedup capped at some point (it helps until something else becomes the bottleneck), no effect (the code is not on the critical path), or negative effect (speeding it up increases lock contention or adds to the critical path). The [[coz-profiler]] is the primary implementation of this technique, with an estimated 17.6% overhead during profiling.

## Prerequisites

- [[cpu-profiling]] — Causal profiling addresses a limitation of traditional CPU profiling (knowing where time is spent vs. what to optimize)
- [[improving-latency]] — Causal profiling measures the impact of speeding up code on overall latency
- [[sampling-vs-instrumentation-profiling]] — Understanding traditional profiling approaches provides context for why causal profiling is needed

## Lectures
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts
- [[coz-profiler]]
- [[virtual-speedup]]
- [[scoz]]
- [[critical-path]]
- [[profiling]]
