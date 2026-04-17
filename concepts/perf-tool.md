---
tags:
  - concept
  - ece459
  - profiling
  - linux
  - perf
lectures:
  - L27
  - L29
prerequisites:
  - "[[sampling-vs-instrumentation-profiling]]"
  - "[[cpu-profiling]]"
---

# perf Tool

`perf` is an interface to the Linux kernel's built-in sample-based profiling using CPU hardware counters. It works per-process, per-CPU, or system-wide and can report the cost of each line of code.

Key usage pattern for Rust:

1. **Compile with debug info**: add `debug = true` under `[profile.release]` in `Cargo.toml` so the release build includes debug symbols
2. **`perf record`**: run the program to sample its execution and produce a data set
3. **Analyze**: use `perf report`, `perf annotate`, or generate a [[flamegraph]]

`perf stat` provides summary counters including task-clock, context-switches, page-faults, cycles, instructions per cycle, branches, and branch-misses.

It is important to profile the release (optimized) build, not the debug build, because the compiler optimizations change the performance characteristics significantly.

## Prerequisites

- [[sampling-vs-instrumentation-profiling]] — perf is a sampling-based profiler; understanding the tradeoffs is essential
- [[cpu-profiling]] — perf is the primary tool for CPU profiling on Linux

## Lectures

- [[L27-Program-Profiling-and-POGO]]
- [[L29-Liar-Liar]]

## Related Concepts

- [[sampling-vs-instrumentation-profiling]]
- [[flamegraph]]
- [[cpu-profiling]]
- [[profiler-lies]]
- [[skid]]
