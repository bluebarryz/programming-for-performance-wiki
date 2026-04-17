---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "29"
prerequisites:
  - "[[sampling-vs-instrumentation-profiling]]"
  - "[[perf-tool]]"
  - "[[out-of-order-execution]]"
---

# Profiler Lies

Profilers are useful tools, but they can mislead in systematic ways. The lies fall into two categories: incorrect data collection and incorrect narratives built from that data. Understanding how profilers work, and their common pitfalls, is essential for drawing correct conclusions.

Data collection lies include [[sampling-aliasing]] (periodic sampling missing events that happen between samples, like the helicopter blade illusion), [[skid]] (interrupt-based sampling attributing costs to the wrong instruction), and [[mfence-profiling-distortion]] (pipeline flushes causing costs to be attributed to flushed instructions rather than the fence). [[long-tail-latency]] events are hidden by low sampling rates that produce flat averages. Even [[hardware-performance-counters]] can be wrong due to speculative execution not rolling back counter values.

Narrative lies include [[gprof-calling-context-lies]] where gprof combines statistical and exact data sources to produce incorrect time attributions across calling contexts. More broadly, looking at percentage breakdowns without considering absolute execution time leads to wrong conclusions: 15% of a 19.6 billion cycle run is far worse than 40% of a 3.66 billion cycle run. The overall lesson is to focus on the metric you actually care about, understand your tools' mechanisms, and validate surprising results with additional evidence.

## Prerequisites

- [[sampling-vs-instrumentation-profiling]] — Understanding how profilers collect data is needed to understand how they can lie
- [[perf-tool]] — Many examples of profiler lies use perf as the profiling tool
- [[out-of-order-execution]] — Pipeline behavior and speculation cause several types of profiler distortion

## Lectures
- [[L29-Liar-Liar]]

## Related Concepts
- [[mfence-profiling-distortion]]
- [[skid]]
- [[sampling-aliasing]]
- [[gprof-calling-context-lies]]
- [[long-tail-latency]]
- [[hardware-performance-counters]]
