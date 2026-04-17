---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "29"
prerequisites:
  - "[[perf-tool]]"
  - "[[out-of-order-execution]]"
---

# Mfence Profiling Distortion

The `mfence` instruction causes a pipeline flush on x86 processors, and profilers drastically underestimate its cost while overestimating the cost of lock-based alternatives. This is one of the most instructive examples of how profilers can lie about performance attribution.

In microbenchmarks comparing `lock inc/dec` versus `mfence` for concurrency control, perf reported that mfence-based synchronization consumed only 15% of runtime while reads consumed 85%. For locks, the split was 40% locks and 52% reads. This made mfence appear far more efficient. But the total cycle counts told a completely different story: no atomic/fence used 2.81 billion cycles, lock inc/dec used 3.66 billion cycles, and mfence used 19.60 billion cycles. The mfence approach was actually 5x worse.

The distortion occurs because mfence causes a pipeline flush, and the resulting stall costs get attributed to the instructions that are flushed (typically the next instructions after the fence), not to the mfence itself. In effect, mfence makes other instructions appear slower, which camouflages its own impact on overall performance. This demonstrates why looking at percentage breakdowns alone is insufficient: a lower percentage of a much larger total time is still worse. Always compare absolute metrics, not just relative proportions.

## Prerequisites

- [[perf-tool]] — The mfence distortion is demonstrated using perf profiling data
- [[out-of-order-execution]] — Pipeline flushes from mfence cause costs to be misattributed to flushed instructions

## Lectures
- [[L29-Liar-Liar]]

## Related Concepts
- [[profiler-lies]]
- [[hardware-performance-counters]]
- [[skid]]
- [[perf-tool]]
