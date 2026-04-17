---
tags:
  - lecture
  - ece459
  - profiling
  - pitfalls
  - accuracy
lecture: 29
title: Liar, Liar
date: 2025-06-01
prerequisite_lectures:
  - "[[L27-Program-Profiling-and-POGO]]"
  - "[[L06-Modern-Processors]]"
---

# L29 - Liar, Liar

Profilers are useful but they can mislead you. This lecture catalogs the ways profiling tools lie, drawing an analogy to evidence in the criminal justice system. Lies from metrics include periodic sampling missing events and `mfence` costs being attributed to other instructions (because pipeline flushes spread the cost around). Skid causes samples to be attributed to the wrong instruction. Long-tail latency distributions are hidden by averages, as demonstrated by a Google disk latency case study. Hardware performance counters can also be inaccurate due to speculative execution (AMD not rolling back perf counters). Finally, `gprof` can produce incorrect calling-context attributions by combining statistical and exact data.

## Prerequisite Lectures
- [[L27-Program-Profiling-and-POGO]] — Need profiling methods to understand how profilers can mislead
- [[L06-Modern-Processors]] — Need out-of-order execution understanding for skid and speculative counter issues

## Concepts Covered

- [[profiler-lies]]
- [[sampling-aliasing]]
- [[mfence-profiling-distortion]]
- [[skid]]
- [[long-tail-latency]]
- [[hardware-performance-counters]]
- [[gprof-calling-context-lies]]
- [[instrumentation-vs-sampling-tradeoffs]]
