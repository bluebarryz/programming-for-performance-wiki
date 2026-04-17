---
tags:
  - lecture
  - ece459
  - profiling
  - observability
  - logging
  - tracing
lecture: L24
title: "Profiling: Observing Operations"
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
---

# L24 - Profiling: Observing Operations

This lecture introduces the observation side of performance optimization, embodying the principle "don't guess, measure." It distinguishes between counters (occurrence counts), profiles (aggregate time breakdowns), and traces (event sequences). Logging is presented as the most fundamental observability tool, with guidance on log levels, timestamps (use UTC), and avoiding PII. Tracing overhead is quantified: tracking every branch is ~20x slower, function timestamps are ~1.2-1.5x, and system call timestamps are <1%. The lecture covers Valgrind for memory tracing, aggregate measures (counters), the importance of context and percentiles when interpreting metrics, the misleading nature of averages with bursty data, and visualization via dashboards.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Performance measurement basics and the "measure first" principle this lecture expands upon

## Concepts Covered

- [[profiling]]
- [[observability]]
- [[logging]]
- [[tracing]]
- [[counters]]
- [[tracing-overhead]]
- [[valgrind]]
- [[aggregate-measures]]
- [[percentiles]]
- [[dashboards]]
- [[premature-optimization]]
