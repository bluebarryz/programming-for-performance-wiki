---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites:
  - "[[relational-algebra]]"
---

# Query Execution Plans

A query execution plan is the concrete strategy a database server uses to carry out a query. Each step in the plan is an evaluation primitive: an algebraic operation annotated with information about how to execute it, such as which algorithm to use or which index to leverage. The sequence of these primitives forms the complete plan.

The database server does not simply execute a fixed series of steps. Instead, it adapts its approach at runtime based on what it estimates will be most efficient. The process follows three steps: (1) parsing and translation of the SQL query into [[relational-algebra]] expressions, (2) optimization by generating alternative plans and selecting the one with the lowest estimated cost, and (3) evaluation by executing the chosen plan. Complex queries are broken into query blocks, each containing a single select-from-where expression, and different blocks can use different strategies.

When there are multiple possible plans -- which there very often are -- the system uses [[query-cost-estimation]] to assess each one. The optimizer does not find the truly optimal plan; it makes estimates and tries to choose the one most likely to be best. A simplified approach focuses on [[join-ordering]] and join algorithms, since joins are typically the most expensive operations. The broader lesson beyond databases is about how to programmatically generate, evaluate, and choose among alternative options for accomplishing a goal.

## Prerequisites

- [[relational-algebra]] — Execution plans are built from relational algebra operations

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[query-cost-estimation]]
- [[relational-algebra]]
- [[equivalence-rules]]
- [[join-ordering]]
- [[plan-caching]]
- [[early-selection-and-projection]]
