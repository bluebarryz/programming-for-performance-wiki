---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "29"
prerequisites:
  - "[[sampling-vs-instrumentation-profiling]]"
  - "[[perf-tool]]"
---

# Sampling Aliasing

Sampling aliasing occurs when periodic sampling systematically misses events that happen between sample points. The term comes from signal processing (the Nyquist theorem), where sampling at too low a frequency produces a distorted view of the underlying signal. The helicopter video illusion is a perfect demonstration: the camera samples at a multiple of the blade rotation frequency, producing images where the blades appear stationary.

In profiling, aliasing means that a periodic interrupt handler or any regularly-timed code can be completely invisible to a sampling profiler if its execution happens to fall between samples. The profiler's samples are individually correct, but the narrative they build is wrong because the sampling rate is too low relative to the frequency of the events of interest. This violates the fundamental assumption of sampling-based profilers: that samples are effectively random and approximate the true time-spent distribution.

The standard tool perf defaults to about 1 KHz sampling and maxes out around 100 KHz, both of which can miss important high-frequency events. Higher sampling rates are limited by the overhead of interrupt processing: too many interrupts and the profiler spends all its time handling interrupts instead of letting the program run. Instrumentation-based tools like SHIM achieve much higher effective rates (10 MHz) by embedding recording code directly in the program rather than relying on interrupts.

## Prerequisites

- [[sampling-vs-instrumentation-profiling]] — Aliasing is a fundamental limitation of sampling-based profiling
- [[perf-tool]] — perf's sampling rate limits make it susceptible to aliasing

## Lectures
- [[L29-Liar-Liar]]

## Related Concepts
- [[profiler-lies]]
- [[instrumentation-vs-sampling-tradeoffs]]
- [[long-tail-latency]]
- [[sampling-vs-instrumentation-profiling]]
