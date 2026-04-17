---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[parallelism]]"
---

# Dependencies in Parallelism

Dependencies are the big problem in parallelization. Several forms:

- A task cannot start processing until it knows what to process -- **coordination overhead**.
- If the problem doesn't have a succinct description, parallelization is difficult.
- Tasks may need to **combine results** with other tasks.
- **Inherently sequential problems**: when a loop iteration depends on the result of the previous iteration, parallelizing the loop is prohibited (though sometimes a parallelizable reformulation exists).
- Code often has a **sequential part and a parallelizable part**. If the sequential part is too long, throwing more processors at the parallelizable part won't help much. This is [[amdahls-law]].

## Prerequisites
- [[parallelism]] — Dependencies are the core difficulty of parallelization

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[parallelism]]
- [[amdahls-law]]
- [[embarrassingly-parallel]]
- [[data-races]]
