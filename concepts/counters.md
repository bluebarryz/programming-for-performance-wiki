---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[observability]]"
---

# Counters

Counters are stored counts of event occurrences: interrupts, cache misses, data bytes written, calls to a function, user logins, and so on. Keeping track of these numbers is relatively inexpensive compared to other observability approaches, so counting every occurrence of an event is plausible. Counters are a form of aggregation -- at the end of the program (or period), you have a total number rather than a detailed trace.

Many profiling tools rely heavily on counters. The sum is the simplest form, but counters also serve as the basis for [[aggregate-measures]] like averages, rates, and percentages. A counter and any data derived from it takes much less space than a trace. The tradeoff is that counters lose the detail of individual events -- you know how many times something happened, but not the sequence or timing of each occurrence.

## Prerequisites
- [[observability]] — Counters are one of the three core observability approaches

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[aggregate-measures]]
- [[observability]]
- [[logging]]
- [[tracing]]
- [[dashboards]]
