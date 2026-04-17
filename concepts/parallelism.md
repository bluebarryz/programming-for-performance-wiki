---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[bandwidth-vs-latency]]"
---

# Parallelism

Rather than (or in addition to) making each thing faster, you can do more things at a time. CPU clock speeds have plateaued, so it is often easier to throw more resources (CPUs) at a problem.

**Why parallelism?** There are limits to how fast you can do each thing. Parallelism improves bandwidth but not latency.

**Different kinds of parallelism:** Different problems suit different parallelization strategies. Web servers easily parallelize simultaneous requests; linked list traversal does not.

**Hardware for parallelism:** Multicore processors, SMP systems, clusters, vector processing units (SIMD), GPUs. Each has different communication latencies.

**Pipelining** is a related concept: splitting a task into subtasks and executing them in parallel, like an assembly line.

Parallelism complicates correctness: there is no longer a total ordering of events, only a partial ordering. This introduces [[data-races]], [[deadlocks]], and stale data problems.

## Prerequisites
- [[bandwidth-vs-latency]] — Parallelism improves bandwidth, not latency; understanding this distinction is essential

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[bandwidth-vs-latency]]
- [[pipelining]]
- [[embarrassingly-parallel]]
- [[dependencies-in-parallelism]]
- [[data-races]]
- [[deadlocks]]
- [[amdahls-law]]
- [[fearless-concurrency]]
