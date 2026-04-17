---
tags:
  - lecture
  - ece459
  - dependencies
  - speculation
  - parallelism
lecture: L13
title: "Dependencies and Speculation"
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
  - "[[L06-Modern-Processors]]"
---

# L13 -- Dependencies and Speculation

This lecture covers how dependencies between computations limit parallelization. It distinguishes loop-carried dependencies (where each iteration depends on the previous) from memory-carried dependencies (where the result depends on the order of memory accesses). The concept of critical paths is introduced. The lecture then presents speculation as a technique to break dependencies: speculative execution (starting work that may not be needed) and value speculation (guessing a value and computing ahead). It also covers software transactional memory (STM) as a related approach that speculatively applies changes and rolls back on conflict.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Parallelism fundamentals needed to understand why dependencies limit parallel execution
- [[L06-Modern-Processors]] — Pipelining and ILP concepts needed for understanding how dependencies stall execution

## Concepts Covered

- [[dependencies]]
- [[loop-carried-dependencies]]
- [[memory-carried-dependencies]]
- [[critical-path]]
- [[speculative-execution]]
- [[value-speculation]]
- [[software-transactional-memory]]
- [[side-effects]]
