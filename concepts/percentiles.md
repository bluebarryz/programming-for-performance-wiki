---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[aggregate-measures]]"
---

# Percentiles

Percentiles supplement averages as aggregate measures by revealing the distribution of values. While the average response time might be 1.27 seconds, the 95th percentile tells you that 95% of requests complete within a certain time, exposing the long tail that averages hide. Looking at maximum and 95th percentile values helps answer whether time limits are being met for the vast majority of requests, not just on average.

This matters when evaluating whether a system meets its performance targets. If there is a hard deadline (e.g., a transaction must return within 1 second), an average below the deadline is insufficient -- you need to know what percentage of requests actually miss it. Percentiles provide that information directly, making them essential for [[evaluating-load-test-success]] and setting meaningful service level objectives.

## Prerequisites
- [[aggregate-measures]] — Percentiles supplement averages as a way to summarize aggregate data

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[aggregate-measures]]
- [[counters]]
- [[evaluating-load-test-success]]
- [[dashboards]]
