---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "29"
prerequisites:
  - "[[perf-tool]]"
  - "[[speculation]]"
  - "[[cpu-profiling]]"
---

# Hardware Performance Counters

Hardware performance counters are CPU-level registers that automatically track events such as cycles, instructions executed, cache misses, branch mispredictions, and context switches. They require no program modification or interruption to collect data, making them a low-overhead source of profiling information. Tools like [[perf-tool]] expose these counters to users.

Counters are faster than measuring wall-clock time and roughly five orders of magnitude more deterministic. To maximize their determinism, practitioners disable Address Space Layout Randomization (which affects hash table layouts via randomized pointer addresses), subtract time spent processing interrupts (IRQs), and profile a single thread when possible.

Despite their precision, counters can still lie. A notable example involves AMD processors that speculate past atomic operations and then roll back the speculation on failure, but fail to roll back the performance counters. This means the counters record work from speculative execution that was ultimately discarded. Post-Spectre, a hidden model-specific register ("SpecLockMap") was introduced to disable speculating past atomics, which also affects counter accuracy. These quirks mean that even hardware-level measurements require careful interpretation.

## Prerequisites

- [[perf-tool]] — perf exposes hardware performance counters to users
- [[speculation]] — Speculative execution causes counters to record work that is ultimately discarded
- [[cpu-profiling]] — Hardware counters are the underlying mechanism for CPU profiling tools

## Lectures
- [[L29-Liar-Liar]]

## Related Concepts
- [[perf-tool]]
- [[profiler-lies]]
- [[mfence-profiling-distortion]]
- [[cpu-profiling]]
