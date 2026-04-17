---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites:
  - "[[query-execution-plans]]"
  - "[[database-metadata-and-histograms]]"
---

# Query Cost Estimation

Query cost estimation is the process by which a database optimizer evaluates how expensive each candidate [[query-execution-plans|execution plan]] would be. The dominant cost factor is disk I/O: the number of block transfers (data moved in and out of memory) and the number of disk seeks (repositioning the read head). CPU time is nonzero but typically ignored for simplicity.

The estimation assumes a worst-case memory scenario: only one block per table can be in memory at a time. If more data is actually in memory, the real cost will be lower than the estimate (which is better than the reverse). Several factors affect actual wall-clock time beyond the estimate: system load from concurrent operations, what is already in the buffer cache, and data layout on disk (sequential packing reduces seeks, distribution across multiple disks enables parallel reads).

Estimates are based on [[database-metadata-and-histograms|metadata and histograms]], and the assumptions behind them are very often wrong. This is acceptable -- the goal is not to be perfect, but to be better than not optimizing at all. Even picking the second or fifth best plan is fine as long as it is close to the best. The optimizer must also balance the cost of optimization itself against potential savings: analyzing alternatives is not free, and it is possible to waste more time on analysis than a better plan would save. A common strategy is to set a time limit for optimization proportional to how expensive the query appears.

## Prerequisites

- [[query-execution-plans]] — Cost estimation evaluates candidate execution plans
- [[database-metadata-and-histograms]] — Estimates are based on statistical metadata about tables

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[query-execution-plans]]
- [[database-metadata-and-histograms]]
- [[join-ordering]]
- [[equivalence-rules]]
- [[plan-caching]]
