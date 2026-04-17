---
tags:
  - concept
  - ece459
  - parallelism
  - performance
  - gpu
lectures:
  - L17
  - L21
prerequisites:
  - "[[parallelism]]"
  - "[[concurrency-vs-parallelism]]"
---

# Data Parallelism

Data parallelism is one of two broad categories of parallelism (alongside [[task-parallelism]]). In data parallelism, multiple threads perform the **same** operation on separate data items. The analogy is a call center where every worker handles support calls in the same way.

For example, given a large array where every element needs to be doubled, you assign part of the array to each thread and each thread does the same thing: double its elements.

Data parallelism is the natural fit for [[simd]] instructions, which apply a single instruction to an entire vector of data at once. It is complementary to thread-based parallelism and works well on small data sets where thread startup cost would be too high.

In GPU computing, data parallelism is the central feature: you evaluate a [[cuda-kernel]] at a set of points (the [[work-items-and-index-space|index space]]), where each point represents a data element such as a body in an N-body simulation or a pixel in an image.

## Prerequisites

- [[parallelism]] — Data parallelism is a specific category of parallelism
- [[concurrency-vs-parallelism]] — Understanding the distinction between concurrency and parallelism

## Lectures

- [[L17-Mostly-Data-Parallelism]]
- [[L21-GPU-Programming]]

## Related Concepts

- [[task-parallelism]]
- [[simd]]
- [[auto-vectorization]]
- [[cuda-kernel]]
- [[work-items-and-index-space]]
