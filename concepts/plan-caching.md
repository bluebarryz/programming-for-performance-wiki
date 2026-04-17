---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites:
  - "[[query-execution-plans]]"
  - "[[query-cost-estimation]]"
  - "[[caching]]"
---

# Plan Caching

Plan caching is a database optimization technique where the execution plan for a query is saved and reused when the same query (or a structurally identical query with different parameter values) is submitted again. In any busy system, common queries are repeated frequently with only slightly different parameters -- for example, many students querying their course enrollments with different student ID numbers.

When a cached plan is reused, the optimizer skips the cost of generating and evaluating alternative plans, which can be significant for complex queries. The results will differ between executions, and the actual cost may vary (one student takes 7 courses, another takes 5), but the plan itself -- which tables to scan, which indexes to use, in what order to join -- remains appropriate. If the query has been executed before, the actual execution time from the previous run can replace the original estimate, providing an even more accurate cost model (or an average of the last n executions if there is high variability).

Plan caching is an instance of the broader principle of remembering already-computed results to avoid redundant work. It intersects with the [[observe-and-change]] strategy: if the optimizer notices that a cached plan is performing poorly (perhaps because the underlying data distribution has changed), it can invalidate the cache and re-optimize.

## Prerequisites

- [[query-execution-plans]] — Plan caching saves and reuses previously generated execution plans
- [[query-cost-estimation]] — Cached plans can use actual execution times to improve cost estimates
- [[caching]] — Plan caching is an instance of the broader caching principle

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[query-execution-plans]]
- [[query-cost-estimation]]
- [[observe-and-change]]
- [[caching]]
