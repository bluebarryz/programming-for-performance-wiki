---
tags:
  - lecture
  - ece459
  - algorithms
  - concurrency
  - parallelism
lecture: 9
title: Algorithms, Concurrency, and Parallelism
date: 2025-06-02
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
---

# L09 - Algorithms, Concurrency, and Parallelism

This lecture bridges algorithmic thinking and parallel programming. It starts with algorithm optimization strategies (BUD: Bottlenecks, Unnecessary Work, Duplicated Work), discusses the "accidentally quadratic" pitfall, then distinguishes concurrency from parallelism. The core quantitative content is Amdahl's Law and Gustafson's Law for reasoning about parallel speedup limits. It closes with practical parallelization concerns: locking, memory allocators, overhead, and thread pools.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Parallelism fundamentals and Amdahl's Law introduction that this lecture formalizes

## Concepts Covered

- [[algorithm-optimization]]
- [[accidentally-quadratic]]
- [[concurrency-vs-parallelism]]
- [[amdahls-law]]
- [[gustafsons-law]]
- [[locking-and-synchronization]]
- [[memory-allocators]]
- [[thread-pools]]
- [[parallelization-overhead]]
