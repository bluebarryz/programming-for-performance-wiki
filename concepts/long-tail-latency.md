---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "29"
prerequisites:
  - "[[sampling-vs-instrumentation-profiling]]"
  - "[[improving-latency]]"
---

# Long-Tail Latency

Long-tail latency refers to the phenomenon where a small percentage of requests take dramatically longer than the majority, creating a "long tail" in the latency distribution. Sampling profilers are particularly bad at detecting these events because they aggregate data into averages that mask the outliers.

A concrete example from Google involved 64 KB disk reads where most reads completed quickly (cached in RAM or disk cache), but the 99th percentile latency was 696ms with peaks at 250, 500, 750, and 1000ms. The cause turned out to be kernel CPU throttling: when processes exceeded their CPU usage quota, the kernel put all relevant threads to sleep until the next quarter-second boundary. This was happening on 25% of Google's disk servers for an average of half an hour per day, with periods of high latency as long as 23 hours, and had gone undetected for three years.

For distributed computations like search, long-tail latency is especially damaging because the overall result can only be as fast as the slowest component. This makes the tail, not the average, the metric that matters. Standard sampling profilers operating at low frequencies (e.g., perf at 1 KHz or even 100 KHz) produce flat, uninformative graphs for these events. Higher-resolution tools using instrumentation (like SHIM at 10 MHz) are needed to reveal the true latency distribution.

## Prerequisites

- [[sampling-vs-instrumentation-profiling]] — Sampling profilers are particularly bad at detecting long-tail events
- [[improving-latency]] — Understanding latency as a performance metric is needed to appreciate why tail latency matters

## Lectures
- [[L29-Liar-Liar]]

## Related Concepts
- [[profiler-lies]]
- [[sampling-aliasing]]
- [[instrumentation-vs-sampling-tradeoffs]]
