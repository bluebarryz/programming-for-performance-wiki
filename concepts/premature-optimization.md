---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[profiling]]"
---

# Premature Optimization

The famous Donald Knuth quote warns: "Programmers waste enormous amounts of time thinking about, or worrying about, the speed of noncritical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%."

The key takeaway is "don't guess, measure." Without profiling tools, developers end up guessing which parts of their program are slow and optimizing the wrong things. Our intuition about what is fast and what is slow is often wrong, at both macro and micro levels. The course transitions from "let's speed this up" techniques to first identifying what actually needs to be sped up, using [[observability]] tools like [[logging]], [[counters]], [[tracing]], and profilers to make data-driven optimization decisions.

## Prerequisites
- [[profiling]] — The cure for premature optimization is measuring before optimizing

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[observability]]
- [[cpu-profiling]]
- [[counters]]
- [[logging]]
