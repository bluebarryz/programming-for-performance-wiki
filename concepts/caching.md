---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[improving-latency]]"
---

# Caching

A hybrid between "do less work" and "be smarter." You store the results of expensive, side-effect-free operations (I/O or computation) and reuse them as long as they are still valid.

The lecture illustrates this with a real-world anecdote: a report that was timing out at 30 minutes. By caching exchange rates (which don't change for a retroactive report) and caching articles (loading all at once instead of repeatedly from the database), combined with doing less work (fetching only needed fields, updating only changed parts), the report was brought under 30 minutes.

Caching is important in certain situations and comes up repeatedly throughout the course, including in hardware contexts (CPU caches, cache coherency).

## Prerequisites
- [[improving-latency]] — Caching is one of the key strategies for improving latency

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[improving-latency]]
- [[profiling]]
- [[scalability]]
