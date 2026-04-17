---
tags:
  - concept
  - ece459
  - L13
  - parallelism
  - scheduling
prerequisites:
  - "[[dependencies-in-parallelism]]"
  - "[[parallelism]]"
---

# Critical Path

The critical path is the minimum amount of time to complete a task, taking dependencies into account. It represents the longest chain of dependent operations that must execute sequentially.

In a dependency graph, tasks that are not on the critical path can potentially run in parallel with critical-path tasks. For example, if B depends on A and D depends on B and C, but C has no dependencies, then C can run in parallel with A and B. The critical path is Start -> A -> B -> D -> Finish.

Critical path analysis helps identify what can run in parallel and informs scheduling decisions. Expected execution times for different parallelization strategies can be computed from the critical path.

## Prerequisites

- [[dependencies-in-parallelism]] — The critical path is defined by chains of dependencies
- [[parallelism]] — Critical path analysis determines what can run in parallel

## Lectures

- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[dependencies]]
- [[loop-carried-dependencies]]
- [[memory-carried-dependencies]]
