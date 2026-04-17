---
tags:
  - concept
  - ece459
  - algorithms
lectures:
  - "09"
prerequisites:
  - "[[algorithm-optimization]]"
---

# Accidentally Quadratic

Accidentally quadratic behaviour occurs when two linear operations are combined in a way that produces O(n^2) runtime. Since many problems are fundamentally linear -- take an item, process it, move on -- this quadratic blowup is particularly insidious because the code may look correct and even perform fine on small inputs.

A classic example from the Rust ecosystem involves Robin-Hood Hashing with open addressing and linear probing. When copying data to a new hash table that is nearly full, each insertion requires a linear scan to find a free bucket. Since this scan happens inside the linear loop of copying all items, the result is quadratic behaviour. The problem disappears after a resize but recurs as the table fills again. More generally, inserting a large number of elements into an almost-full hash table becomes quadratic because each insertion requires a linear search for a free slot.

The key takeaway is that even well-known "optimal" data structures like hashmaps can exhibit accidentally quadratic behaviour under certain conditions. Real-world code has nuance and unexpected interactions, so the normally-best approach is not always the best in every situation. When algorithmic improvement cannot reduce the complexity further (some problems are inherently linear or worse), the solution is to apply parallelism to get the work done faster.

## Prerequisites

- [[algorithm-optimization]] — Accidentally quadratic is a pitfall encountered during algorithm optimization

## Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]]

## Related Concepts
- [[algorithm-optimization]]
- [[concurrency-vs-parallelism]]
- [[parallelization-overhead]]
