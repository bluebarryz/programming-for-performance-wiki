---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - L27
  - L29
prerequisites:
  - "[[cpu-profiling]]"
  - "[[bottleneck-analysis]]"
---

# Sampling vs Instrumentation Profiling

Profiling tools fall into two categories:

**Sampling-based** (e.g., `gprof`, `perf`): periodically stops the system (e.g., every 100ms for gprof) and records what it is doing. This is low-overhead but can miss events that happen between samples. The main assumptions are that samples are "random" and that the sample distribution approximates the actual time-spent distribution.

**Instrumentation-based** (or probe-based/predicate-based): queries system state under specific conditions, like conditional breakpoints. More precise but potentially more expensive because it adds code to the program. Examples include DTrace and Nethercote's `counts` tool.

Sampling-based profilers can miss things entirely, while instrumentation-based profilers distort the system under observation. Understanding these tradeoffs is essential to avoid being misled by profiling results.

## Prerequisites

- [[cpu-profiling]] — Sampling and instrumentation are the two main approaches to CPU profiling
- [[bottleneck-analysis]] — Profiling approach selection assumes you have already identified the CPU as the bottleneck

## Lectures

- [[L27-Program-Profiling-and-POGO]]
- [[L29-Liar-Liar]]

## Related Concepts

- [[perf-tool]]
- [[cpu-profiling]]
- [[profiler-lies]]
- [[instrumentation-vs-sampling-tradeoffs]]
