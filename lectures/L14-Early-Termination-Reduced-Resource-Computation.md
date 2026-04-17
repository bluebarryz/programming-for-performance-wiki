---
tags:
  - lecture
  - ece459
  - early-termination
  - reduced-resource
  - performance
lecture: L14
title: "Early Termination, Reduced-Resource Computation"
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
  - "[[L09-Algorithms-Concurrency-and-Parallelism]]"
---

# L14 -- Early Termination, Reduced-Resource Computation

This lecture covers two strategies for trading accuracy for time. Early phase termination involves skipping work that is deemed unnecessary or too slow -- killing slow threads at barriers, pruning search spaces (e.g., travelling salesperson), or stopping once a "good enough" solution is found. Reduced-resource computation involves intentionally using lower precision (e.g., float vs double, fast inverse square root from Quake III) or approximations (e.g., centre-of-mass bins in the N-body problem). Loop perforation -- skipping loop iterations and compensating -- is also covered.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Performance measurement basics needed to evaluate accuracy-time tradeoffs
- [[L09-Algorithms-Concurrency-and-Parallelism]] — Parallel execution model needed for understanding barrier-based early termination

## Concepts Covered

- [[early-phase-termination]]
- [[reduced-resource-computation]]
- [[fast-inverse-square-root]]
- [[n-body-problem]]
- [[loop-perforation]]
