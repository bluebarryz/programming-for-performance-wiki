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

# Equivalence Rules

Equivalence rules are transformation rules that allow a query optimizer to rewrite a [[relational-algebra]] expression into an equivalent one that produces the same result but may have a different (and potentially much lower) execution cost. They resemble expression transformations from mathematics -- for example, just as multiplication commutes (3 x 10 x 7 = 7 x 10 x 3), join operations commute (r1 join r2 = r2 join r1), and selections can sometimes be pushed through joins.

The query optimizer systematically generates equivalent expressions using these rules, but since enumerating all possible transformations and evaluating each one can itself take non-trivial time, the optimizer typically takes shortcuts rather than brute-forcing every possibility. One technique is to re-use common subexpressions to reduce the space used when representing expressions during evaluation -- an application of remembering already-computed results.

The key insight for performance is that while all equivalent expressions produce the same result, their costs can vary enormously. For example, performing a selection before a join (pushing selection down) can reduce the join input from hundreds of rows to one. The optimizer uses equivalence rules to explore this space of alternatives, combined with [[query-cost-estimation]] to choose the cheapest plan.

## Prerequisites

- [[relational-algebra]] — Equivalence rules transform relational algebra expressions into equivalent forms

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[relational-algebra]]
- [[query-execution-plans]]
- [[query-cost-estimation]]
- [[early-selection-and-projection]]
- [[join-ordering]]
