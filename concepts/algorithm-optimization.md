---
tags:
  - concept
  - ece459
  - algorithms
lectures:
  - "09"
prerequisites:
  - "[[improving-latency]]"
  - "[[profiling]]"
---

# Algorithm Optimization

Algorithm optimization in ECE 459 focuses on improving the runtime performance of code by refining the algorithm itself before resorting to parallelism or hardware-level tricks. The approach starts with a correct, possibly brute-force solution, then refines it using the BUD framework from Cracking the Coding Interview: identify Bottlenecks (the rate-limiting phase), Unnecessary Work (effort that can be skipped, like continuing to search after finding the answer), and Duplicated Work (recomputing values that could be memoized or restructured).

Big-O complexity analysis is the standard tool, but real-world considerations matter. If n is small enough, a theoretically worse algorithm may perform just as well. Sorting a large array or building a hashmap is worthwhile if the data will be queried many times, but overkill for a single search. Additionally, algorithmic complexity improvements have inherent limits -- some problems, like grading every exam paper, are fundamentally linear and cannot be improved algorithmically.

When algorithmic improvements are exhausted, the next step is parallelism. Dividing the work across multiple processors can reduce wall-clock time even when the total work remains the same. This transition from algorithm optimization to parallel execution is a central theme of the course.

## Prerequisites

- [[improving-latency]] — Algorithm optimization is one of the strategies for reducing latency from L01
- [[profiling]] — Profiling identifies the bottlenecks that algorithm optimization targets

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]

## Related Concepts
- [[accidentally-quadratic]]
- [[amdahls-law]]
- [[concurrency-vs-parallelism]]
