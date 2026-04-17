---
tags:
  - concept
  - ece459
  - query-optimization
lectures:
  - L19
prerequisites: []
---

# Database Metadata and Histograms

Database query optimization relies on statistical metadata to estimate the cost of different execution plans. Key metadata includes: the number of rows in a table (n_r), the number of disk blocks containing a table (b_r), the size in bytes of a table (l_r), the number of rows that fit into one block (f_r), the number of distinct values for an attribute (V(A, r)), and the height of an index (h_r,i). Some of these values are derived -- for example, f_r is simply n_r divided by b_r.

Histograms provide more fine-grained statistical information by dividing attribute values into ranges and recording how many tuples fall within each range. They do not necessarily have an even distribution. A histogram of salaries, for instance, might reveal that 10 employees earn above $100,000, allowing the optimizer to accurately estimate the result size of a query filtering on that range. Histograms are compact and provide much better estimates than assuming uniform distribution.

These statistics may be slightly out of date depending on when metadata updates are last performed, but even approximate values are far better than no information at all. The more exact values available, the better the optimizer can estimate [[query-cost-estimation]] and choose an efficient [[query-execution-plans|query execution plan]].

## Prerequisites

None — foundational concept.

## Lectures

- [[L19-Query-Optimization]]

## Related Concepts

- [[query-cost-estimation]]
- [[query-execution-plans]]
- [[equivalence-rules]]
- [[join-ordering]]
