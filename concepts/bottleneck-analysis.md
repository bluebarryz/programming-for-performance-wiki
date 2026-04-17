---
tags:
  - concept
  - ece459
  - profiling
  - bottlenecks
lectures:
  - L26
prerequisites:
  - "[[profiling]]"
  - "[[memory-hierarchy]]"
---

# Bottleneck Analysis

Before assuming the CPU is the problem, you should systematically check each potential bottleneck device. The five main categories of performance bottleneck are:

1. **CPU** -- diagnosed with `top` and load averages
2. **Memory** -- diagnosed by checking swap activity with `vmstat`
3. **Disk** -- diagnosed with `iostat` (check `%util`)
4. **Network** -- diagnosed with `nload` and `traceroute`
5. **Locks** -- diagnosed by looking for unexpectedly low CPU usage with many blocked threads

It is a mistake to theorize before collecting data. Even after identifying a bottleneck, fixing it is a separate challenge -- sometimes the correct answer is that the hardware is simply insufficient.

A reported performance problem may also turn out to be a programming error (e.g., doing heavy work on the UI thread) rather than a resource bottleneck.

## Prerequisites

- [[profiling]] — Understanding that profiling is how you identify performance problems
- [[memory-hierarchy]] — Knowing how memory levels affect performance helps diagnose memory and cache bottlenecks

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[cpu-load-average]]
- [[memory-bottleneck-diagnosis]]
- [[disk-bottleneck-diagnosis]]
- [[network-bottleneck-diagnosis]]
- [[lock-contention-diagnosis]]
- [[cpu-profiling]]
