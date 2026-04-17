---
tags:
  - lecture
  - ece459
  - performance
  - database
  - query-optimization
lecture: 19
title: Query Optimization
prerequisite_lectures: []
---

# L19 - Query Optimization

This lecture uses database query optimization as an example of runtime decision-making for performance. It covers how a database server parses SQL into relational algebra, generates query execution plans, and estimates their cost using metadata and histograms. The lecture discusses equivalence rules for transforming queries, join ordering (and its combinatorial explosion), heuristic shortcuts (early selection, early projection, time limits), plan caching, and join elimination. The broader lesson is about programmatically choosing among alternative execution strategies at runtime.

## Prerequisite Lectures
None -- this lecture is relatively standalone, using database query optimization as a case study in runtime decision-making.

## Concepts Covered

- [[query-execution-plans]]
- [[relational-algebra]]
- [[query-cost-estimation]]
- [[equivalence-rules]]
- [[join-ordering]]
- [[database-metadata-and-histograms]]
- [[early-selection-and-projection]]
- [[plan-caching]]
- [[join-elimination]]
