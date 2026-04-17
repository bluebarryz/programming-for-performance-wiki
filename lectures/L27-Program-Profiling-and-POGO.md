---
tags:
  - lecture
  - ece459
  - profiling
  - pogo
  - optimization
lecture: 27
title: Program Profiling and POGO
date: 2024-09-16
prerequisite_lectures:
  - "[[L26-Finding-Bottleneck-Devices]]"
  - "[[L18-Compiler-Optimizations]]"
---

# L27 - Program Profiling and POGO

This lecture covers the mechanics of program profiling and Profile-Guided Optimization (POGO). It contrasts invasive (logging-based) profiling with tool-based approaches, and distinguishes sampling-based profiling (e.g., `perf`) from instrumentation-based profiling. The `perf` tool is demonstrated for Rust programs. The second half covers POGO: a multi-step compilation process where the program is first instrumented, then run with real-world data to collect training profiles, and finally recompiled using that data to produce a better-optimized binary. POGO optimizations include inlining decisions, function/block layout for page locality, and virtual call speculation.

## Prerequisite Lectures
- [[L26-Finding-Bottleneck-Devices]] — Need bottleneck analysis before diving into CPU-level profiling
- [[L18-Compiler-Optimizations]] — Need compiler optimization fundamentals for Profile-Guided Optimization

## Concepts Covered

- [[invasive-profiling]]
- [[sampling-vs-instrumentation-profiling]]
- [[perf-tool]]
- [[flamegraph]]
- [[profiling-best-practices]]
- [[profile-guided-optimization]]
- [[pogo-probes]]
- [[pogo-training]]
- [[pogo-optimizations]]
- [[hot-and-cold-code]]
- [[call-graph-path-profiling]]
- [[page-locality]]
- [[devirtualization]]
