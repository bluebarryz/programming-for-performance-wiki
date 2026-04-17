---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - L27
prerequisites:
  - "[[cpu-profiling]]"
---

# Invasive Profiling

Invasive profiling refers to modifying the source code of a program to add instrumentation such as log or debug statements. This approach has significant drawbacks:

- It changes the program being observed, potentially altering its performance characteristics
- The instrumentation itself (e.g., logging) is slow
- Manual accounting of timing data is tedious and error-prone
- It only works when functions are slow enough to measure by hand (e.g., a single function taking minutes)

Despite its limitations, invasive profiling can be useful for coarse-grained investigation, such as identifying which block of a long-running function is slow. For systematic profiling, tool-based approaches like [[perf-tool]] or [[flamegraph]]s are strongly preferred.

## Prerequisites

- [[cpu-profiling]] — Invasive profiling is a crude approach to CPU profiling, contrasted with tool-based methods

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[sampling-vs-instrumentation-profiling]]
- [[perf-tool]]
- [[profiling-best-practices]]
