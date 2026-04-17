---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites: []
---

# Profiling

You cannot successfully make code faster if you do not know why it is slow. Intuition about where time is spent is often wrong -- sometimes off by several orders of magnitude. This is a specific instance of the engineering rule: "Don't guess; measure."

Run your program with realistic workloads under a profiling tool to figure out where time is actually going. It is okay to have a theory as a starting point, but test it.

Profiling is key at multiple stages: before optimizing (to find bottlenecks), after optimizing (to verify improvements via controlled experiments), and when the code might be I/O-bound rather than CPU-bound. The course discusses profiling tools in more detail later.

This principle also appears in Law 4 of Crista's Laws: "Performance improvements = log(controlled experiments)."

## Prerequisites
None — foundational concept.

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[improving-latency]]
- [[laws-of-performant-software]]
- [[bandwidth-vs-latency]]
