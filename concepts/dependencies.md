---
tags:
  - concept
  - ece459
  - L13
  - parallelism
prerequisites:
  - "[[parallelism]]"
  - "[[dependencies-in-parallelism]]"
---

# Dependencies

A dependency prevents parallelization when the computation XY produces a different result from YX -- there is a required ordering. If you need the result of an earlier step, you must wait for it before proceeding.

Two kinds of dependencies:
- [[loop-carried-dependencies]] -- an iteration depends on the result of a previous iteration
- [[memory-carried-dependencies]] -- the result depends on the order of memory accesses

Many computations have no dependencies and can be done in any order or concurrently. The key is to identify which computations truly depend on each other and which are independent. The [[critical-path]] represents the minimum time to complete all dependent work.

Dependencies can sometimes be broken using [[speculative-execution]] or [[value-speculation]].

## Prerequisites

- [[parallelism]] — Dependencies are what prevent parallelization
- [[dependencies-in-parallelism]] — L01 introduction to the idea that dependencies limit parallel execution

## Lectures

- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[loop-carried-dependencies]]
- [[memory-carried-dependencies]]
- [[critical-path]]
- [[speculative-execution]]
- [[value-speculation]]
