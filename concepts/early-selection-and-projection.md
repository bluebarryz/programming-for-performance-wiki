---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites:
  - "[[relational-algebra]]"
  - "[[query-execution-plans]]"
---

# Early Selection and Projection

Early selection and early projection are heuristic rules used by database query optimizers to reduce the amount of data flowing through a query execution plan. Selection filters rows, and projection removes unneeded columns. Performing both as early as possible reduces the size of intermediate results, meaning less input to subsequent operations like joins.

Early selection is almost always beneficial: it can cut a relation from a very large number of tuples to relatively few, or even one. There are exceptions -- for instance, if the query involves a selection on a join of r and s where only attributes of s are wanted, if r is small and there is an index on the join attributes of s but not on the selection columns, then doing the selection first would throw away useful index information and force a table scan.

Early projection follows the same logic: discarding unneeded columns sooner means less data to process. However, a projection can be harmful if it removes an attribute needed for a later join. For example, if the join attribute is not part of the final output, it must still be retained until the join is completed. These heuristics are part of the broader strategy of [[query-execution-plans]] where the optimizer balances reducing intermediate data against preserving information needed by later operations.

## Prerequisites

- [[relational-algebra]] — Selection and projection are relational algebra operations
- [[query-execution-plans]] — Early selection/projection reduces intermediate result sizes in execution plans

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[query-execution-plans]]
- [[equivalence-rules]]
- [[relational-algebra]]
- [[join-ordering]]
