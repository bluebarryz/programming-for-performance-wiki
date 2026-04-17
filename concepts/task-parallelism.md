---
tags:
  - concept
  - ece459
  - parallelism
  - performance
lectures:
  - L17
prerequisites:
  - "[[parallelism]]"
  - "[[concurrency-vs-parallelism]]"
---

# Task Parallelism

Task parallelism is one of two broad categories of parallelism (alongside [[data-parallelism]]). In task parallelism, multiple threads perform **different** operations on separate data items. The analogy is an assembly line, where each worker does a different thing.

For example, one thread renders video frames while another thread compresses frames and combines them into a movie file.

## Prerequisites

- [[parallelism]] — Task parallelism is a specific category of parallelism
- [[concurrency-vs-parallelism]] — Understanding the distinction between concurrency and parallelism

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[data-parallelism]]
- [[simd]]
