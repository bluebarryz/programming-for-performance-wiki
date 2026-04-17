---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites:
  - "[[join-ordering]]"
  - "[[equivalence-rules]]"
  - "[[relational-algebra]]"
---

# Join Elimination

Join elimination is a query optimization technique that replaces a query containing a join (expected to be expensive) with an equivalent query that does not require the join, or that converts a join into a nested subquery on the theory that two smaller queries may be easier to execute than one large join. This goes beyond simply choosing the best execution route -- it rewrites the original request to be structurally different.

The optimizer performs this work because SQL is a declarative language: the user specifies the desired result, not the steps to produce it. If there is a more efficient formulation, the database server should find and use it, just as a compiler transparently replaces code with a faster equivalent. Database constraints such as foreign keys and NOT NULL are valuable here because they give the optimizer information needed to prove that a join can be safely eliminated. For example, knowing that a foreign key relationship guarantees exactly one matching row allows the optimizer to skip the join entirely.

The more complex the query, the harder it is to determine whether a join can be eliminated. This is analogous to the library search example: if you know the library keeps only one copy of a book, you can stop looking after finding it. Constraints encode such rules, enabling the optimizer to avoid unnecessary work.

## Prerequisites

- [[join-ordering]] — Join elimination goes further than ordering by removing joins entirely
- [[equivalence-rules]] — Elimination relies on equivalence rules and database constraints to prove joins are unnecessary
- [[relational-algebra]] — Understanding join as a relational algebra operation

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[join-ordering]]
- [[equivalence-rules]]
- [[query-execution-plans]]
- [[relational-algebra]]
