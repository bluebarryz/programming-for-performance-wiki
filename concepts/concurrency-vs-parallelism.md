---
tags:
  - concept
  - ece459
  - concurrency
lectures:
  - "09"
prerequisites:
  - "[[parallelism]]"
  - "[[fearless-concurrency]]"
---

# Concurrency vs Parallelism

Concurrency and parallelism both abandon the total ordering of instructions found in sequential programs, but they serve different purposes. Concurrency is the use of threads to structure programs naturally -- modelling distributed systems, GUIs, or systems where multiple components interact with no inherent ordering. The goal is not increased performance but a more natural program structure.

Parallelism, the focus of ECE 459, is about doing multiple things at the same time to increase throughput. The distinction matters because concurrent programs may be easier to parallelize, but concurrency alone does not guarantee any speedup. A concurrent program running on a single core interleaves tasks but completes no faster in total.

The limits of parallelism are quantified by [[amdahls-law]], which shows that the serial fraction of a program bounds the maximum speedup regardless of how many processors are available. [[gustafsons-law]] offers a more optimistic view by observing that as problem sizes grow, the parallel fraction tends to dominate, making it possible to handle linearly larger problems with linearly more processors.

## Prerequisites

- [[parallelism]] — Understanding parallelism from L01 is needed to distinguish it from concurrency
- [[fearless-concurrency]] — Rust's concurrency model from L03 provides the practical foundation

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]

## Related Concepts
- [[amdahls-law]]
- [[gustafsons-law]]
- [[thread-pools]]
- [[locking-and-synchronization]]
