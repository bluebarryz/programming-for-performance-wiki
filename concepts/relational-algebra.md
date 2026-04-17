---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites: []
---

# Relational Algebra

Relational algebra is the set-theory-based formal language used internally by database systems to represent query operations. SQL queries are translated into relational algebra expressions, which the optimizer can then manipulate using [[equivalence-rules]] to find more efficient formulations. The key operations include selection (choosing rows matching a condition), projection (choosing specific columns), and join (combining rows from multiple tables).

Complex SQL queries are broken into query blocks, each containing a single select-from-where expression along with any group-by and having clauses. Nested subqueries form separate query blocks. For example, a query like `SELECT salary FROM employee WHERE salary > 100000` is one block, while a query with an `IN (SELECT ...)` subquery consists of two blocks that can be optimized independently.

The power of relational algebra for optimization comes from the fact that there are many equivalent ways to express the same query. For instance, given a selection and a join, we can either compute the full join and then select, or select first and then join a much smaller intermediate result. The optimizer uses [[equivalence-rules]] to systematically explore these alternatives and [[query-cost-estimation]] to choose the cheapest plan.

## Prerequisites

None — foundational concept.

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[equivalence-rules]]
- [[query-execution-plans]]
- [[early-selection-and-projection]]
- [[join-ordering]]
