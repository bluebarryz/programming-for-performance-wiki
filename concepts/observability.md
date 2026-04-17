---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[profiling]]"
---

# Observability

Observability is the practice of understanding a program's behavior through measurement and monitoring. It is broader than just profiling -- it includes observing things that may be hard or impossible to quantify. The goal is to collect data on what parts of the code take the most time, which functions are called most frequently, and what is using memory.

The course identifies several key observability tools: [[counters]] (stored counts of occurrences like cache misses or function calls), profiles (higher-level overviews of where time is spent), and [[tracing|traces]] (recordings of the sequence of events showing runtime behavior). These tools serve different purposes: logging is recommended as the single most important tool if you can only have one, counters provide cheap aggregation, and traces give detailed event sequences. The choice of which tools to use depends on the overhead tolerance and the level of detail needed.

## Prerequisites
- [[profiling]] — Observability generalizes the "don't guess, measure" profiling principle

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[logging]]
- [[counters]]
- [[tracing]]
- [[dashboards]]
- [[aggregate-measures]]
- [[premature-optimization]]
