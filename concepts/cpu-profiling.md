---
tags:
  - concept
  - ece459
  - profiling
  - cpu
lectures:
  - L26
  - L27
prerequisites:
  - "[[bottleneck-analysis]]"
  - "[[profiling]]"
---

# CPU Profiling

Most profiling tools and most of the course's discussion focus on CPU profiling -- examining where CPU time is spent. This is because the CPU is the most likely bottleneck and the one most amenable to optimization through code changes.

CPU profiling is predicated on the assumption that CPU time is the limiting factor. Before committing to CPU profiling, you should verify this assumption by checking other potential bottlenecks (memory, disk, network, locks).

The two main approaches to CPU profiling are [[sampling-vs-instrumentation-profiling|sampling-based and instrumentation-based]] profiling.

## Prerequisites

- [[bottleneck-analysis]] — You must first confirm the CPU is the bottleneck before CPU profiling is useful
- [[profiling]] — CPU profiling is a specific application of the general profiling concept

## Lectures

- [[L26-Finding-Bottleneck-Devices]]
- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[bottleneck-analysis]]
- [[perf-tool]]
- [[sampling-vs-instrumentation-profiling]]
- [[profiling-best-practices]]
