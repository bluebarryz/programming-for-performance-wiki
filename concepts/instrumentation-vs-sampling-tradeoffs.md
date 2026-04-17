---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "27"
  - "29"
prerequisites:
  - "[[sampling-vs-instrumentation-profiling]]"
  - "[[cpu-profiling]]"
---

# Instrumentation vs Sampling Tradeoffs

Profiling tools fall into two broad categories: sampling-based and instrumentation-based. Sampling-based profilers (like [[perf-tool]]) periodically stop the system and query its state, for example every 100ms for gprof. Instrumentation-based profilers insert probes into the code that record data when specific conditions are met, functioning like conditional breakpoints.

Sampling-based profilers have lower overhead because they only interrupt the program periodically, but they can miss events that occur between samples. Their accuracy depends on the assumption that samples are random and that the sample distribution approximates the actual time-spent distribution. At low sampling rates, important details like [[long-tail-latency]] events are invisible. Increasing the sampling rate helps but is limited by the overhead of interrupt processing; perf maxes out at around 100 KHz.

Instrumentation-based profilers provide exact data about the events they track but impose higher overhead because every instrumented event triggers recording. They also distort the system under observation: the added code changes cache behavior, timing, and execution characteristics. Tools like DTrace and SHIM use instrumentation to capture events that sampling would miss, achieving much higher effective resolution (e.g., 10 MHz). The choice between approaches depends on whether completeness or low overhead is more important for the specific profiling task.

## Prerequisites

- [[sampling-vs-instrumentation-profiling]] — This concept elaborates on the tradeoffs introduced in L27
- [[cpu-profiling]] — These tradeoffs apply to the choice of CPU profiling tool

## Lectures
- [[L27-Program-Profiling-and-POGO]]
- [[L29-Liar-Liar]]

## Related Concepts
- [[sampling-vs-instrumentation-profiling]]
- [[profiler-lies]]
- [[sampling-aliasing]]
- [[perf-tool]]
