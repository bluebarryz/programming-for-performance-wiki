---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[parallelism]]"
  - "[[dependencies-in-parallelism]]"
---

# Amdahl's Law

Code often contains a sequential part and a parallelizable part. If the sequential part takes too long to execute, then executing the parallelizable part on even an infinite number of processors is not going to speed up the task as a whole. This is known as Amdahl's Law.

Mentioned in L01 as a key limitation of parallelism, with more detailed treatment later in the course. It formalizes the intuition that the sequential portion of a program puts a hard upper bound on the speedup achievable through parallelization.

## Prerequisites
- [[parallelism]] — Amdahl's Law quantifies the limits of parallel speedup
- [[dependencies-in-parallelism]] — The sequential portion that limits speedup comes from dependencies

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[parallelism]]
- [[dependencies-in-parallelism]]
- [[scalability]]
