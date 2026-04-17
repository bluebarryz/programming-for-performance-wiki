---
tags:
  - concept
  - ece459
  - profiling
  - visualization
lectures:
  - L27
  - L28
prerequisites:
  - "[[perf-tool]]"
  - "[[cpu-profiling]]"
---

# Flamegraph

A flamegraph is a visualization of profiling data that shows the call stack over time. Each horizontal bar represents a function, with width proportional to the time spent in that function (including its callees). The y-axis represents stack depth.

Flamegraphs can be generated from `perf record` data or from other profiling tools. CLion's built-in profiler generates flamegraphs directly. [[miri|Miri]] can also produce flamegraph-style output via the `crox` tool for viewing in Chrome dev tools.

Flamegraphs make it easy to visually identify which functions dominate execution time and how the call hierarchy contributes to overall runtime.

## Prerequisites

- [[perf-tool]] — Flamegraphs are typically generated from perf record data
- [[cpu-profiling]] — Flamegraphs visualize CPU profiling results

## Lectures

- [[L27-Program-Profiling-and-POGO]]
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts

- [[perf-tool]]
- [[cpu-profiling]]
- [[miri]]
