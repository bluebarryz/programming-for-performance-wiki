---
tags:
  - concept
  - ece459
  - L13
  - parallelism
  - dependencies
prerequisites:
  - "[[dependencies-in-parallelism]]"
  - "[[data-races]]"
---

# Memory-Carried Dependencies

A memory-carried dependency occurs when the result of a computation depends on the order in which two memory accesses happen. For example, if `f()` adds 50 to a balance and `g()` multiplies by 1.01, the final result differs depending on whether `f` or `g` runs first.

Unlike [[loop-carried-dependencies]], which are about iteration order, memory-carried dependencies are about the order of access to shared memory locations across potentially concurrent operations.

## Prerequisites

- [[dependencies-in-parallelism]] — Understanding that dependencies block parallel execution
- [[data-races]] — Memory-carried dependencies involve concurrent access to shared memory

## Lectures

- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[dependencies]]
- [[loop-carried-dependencies]]
- [[critical-path]]
