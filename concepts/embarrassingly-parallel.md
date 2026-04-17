---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[parallelism]]"
---

# Embarrassingly Parallel

Some domains are "embarrassingly parallel" -- the difficulties of parallelism don't apply to them. For these problems:

- It is easy to communicate the problem to all processors
- The processors don't need to talk to each other to compute
- Getting the answer back is straightforward

The canonical example is Monte Carlo integration, where each processor computes the contribution of a subrange of the integral independently.

These are the easiest problems to parallelize because there are no [[dependencies-in-parallelism]] between tasks.

## Prerequisites
- [[parallelism]] — Embarrassingly parallel is a category of parallel problems

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[parallelism]]
- [[dependencies-in-parallelism]]
- [[amdahls-law]]
