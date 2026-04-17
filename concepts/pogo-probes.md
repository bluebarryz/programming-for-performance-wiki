---
tags:
  - concept
  - ece459
  - pogo
  - instrumentation
lectures:
  - L27
prerequisites:
  - "[[profile-guided-optimization]]"
  - "[[sampling-vs-instrumentation-profiling]]"
---

# POGO Probes

During the instrumentation phase of [[profile-guided-optimization|POGO]], the compiler inserts three types of probes into the generated code:

1. **Function entry probes**: count how many times each function is called
2. **Edge probes**: count transitions at branches (whether the `if` or `else` path is taken)
3. **Value probes**: collect histograms of values (e.g., frequency of values passed to a `match` statement)

These probes record data during training runs, which is then used in the recompile phase to make better optimization decisions. The program runs significantly slower with probes enabled because of the recording overhead.

## Prerequisites

- [[profile-guided-optimization]] — Probes are the instrumentation mechanism used in POGO's first phase
- [[sampling-vs-instrumentation-profiling]] — POGO probes are a form of instrumentation-based profiling

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[profile-guided-optimization]]
- [[pogo-training]]
- [[pogo-optimizations]]
