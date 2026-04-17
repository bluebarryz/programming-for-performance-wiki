---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites:
  - "[[query-cost-estimation]]"
  - "[[equivalence-rules]]"
---

# Join Ordering

Join ordering is the problem of determining the sequence in which join operations should be performed in a multi-table query. For n relations, there are (2(n-1))! / (n-1)! possible join orderings. Even accounting for symmetry (since r1 join r2 = r2 join r1 in relational algebra), the number of possibilities grows explosively. With just 3 relations there are 12 orderings; with 5 or more, exhaustive search becomes impractical.

The optimizer addresses this by using dynamic programming to "remember" the best plan for subsets of the joins. For example, given r1 join r2 join r3 join r4 join r5, the optimizer can compute the best ordering for (r1 join r2 join r3) once and reuse that result when considering further joins with r4 and r5. This reduces the five-relation problem into smaller subproblems. The tradeoff is that the result may be locally optimal but not globally optimal -- if r1 join r4 happens to produce very few tuples, doing that first might be best, but this combination may never be explored if r1 is always grouped with r2 and r3.

The sort order of intermediate results also matters: a sort order is "interesting" if it is useful for a subsequent join. The best plan for a subset is not necessarily the best overall if it produces results sorted on attributes irrelevant to the next join, requiring an extra sort. This increases the complexity of the optimization, though fortunately there are usually not too many interesting sort orders.

## Prerequisites

- [[query-cost-estimation]] — The optimizer uses cost estimates to compare different join orderings
- [[equivalence-rules]] — Join commutativity and associativity rules define the space of possible orderings

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[query-cost-estimation]]
- [[equivalence-rules]]
- [[query-execution-plans]]
- [[join-elimination]]
- [[database-metadata-and-histograms]]
