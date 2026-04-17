---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "29"
prerequisites:
  - "[[sampling-vs-instrumentation-profiling]]"
  - "[[out-of-order-execution]]"
---

# Skid

Skid is a phenomenon in interrupt-based sampling profilers where the instruction pointer recorded in a sample does not correspond to the instruction that actually triggered the sample. As the perf wiki describes it: the instruction pointer stored in each sample designates where the program was interrupted to process the PMU (Performance Monitoring Unit) interrupt, not where the counter actually overflowed.

This results in performance costs being attributed to the wrong instructions. A classic example: a slow load instruction might show 0.1% cost, while a subsequent NOP instruction shows 27.0% cost. The NOP is obviously not expensive; the load is the real culprit, but by the time the interrupt fires and the CPU records the instruction pointer, execution has moved past the load to later instructions.

Modern Intel and AMD x86_64 CPUs offer hardware support for more precise (low- or no-skid) sampling through mechanisms like PEBS (Precise Event-Based Sampling). However, this precise mode may not always be used because it could slow down execution, might not be available for all event types, or could produce even more distorted results in certain scenarios. Awareness of skid is important for correctly interpreting instruction-level profiling results.

## Prerequisites

- [[sampling-vs-instrumentation-profiling]] — Skid is a problem specific to interrupt-based sampling profilers
- [[out-of-order-execution]] — Out-of-order execution causes the instruction pointer to advance past the actual culprit

## Lectures
- [[L29-Liar-Liar]]

## Related Concepts
- [[profiler-lies]]
- [[hardware-performance-counters]]
- [[mfence-profiling-distortion]]
- [[perf-tool]]
