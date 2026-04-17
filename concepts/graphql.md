---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[n-plus-one-query]]"
  - "[[excessive-network-calls]]"
---

# GraphQL

GraphQL is a data query language that lets the caller specify exactly what information they want based on a known schema. Unlike REST APIs where the server determines the endpoints, verbs, and response shape, GraphQL allows clients to request only the fields they need. This avoids the problem of over-fetching (getting seven full invoices when you only need the total field) and under-fetching (needing another endpoint for a different view of the data).

In ECE 459, GraphQL is discussed in the context of the [[n-plus-one-query]] problem. Because GraphQL lets callers compose arbitrary queries against the schema, it is harder for the backend to predict which queries will be executed and therefore harder to optimize with [[eager-loading]]. A naive GraphQL resolver that loads each related entity individually will produce N+1 database queries. The Rust crate `juniper_eager_loading` addresses this by separating the GraphQL model from the data layer and batching related-entity lookups.

The tradeoff with GraphQL is flexibility vs optimization difficulty. REST endpoints can be individually tuned because their access patterns are known, while GraphQL must handle arbitrary query shapes efficiently. Libraries like DataLoader (in various languages) or `juniper_eager_loading` (in Rust) exist specifically to solve this problem.

## Prerequisites

- [[n-plus-one-query]] — GraphQL is discussed in the context of solving the N+1 query problem
- [[excessive-network-calls]] — GraphQL addresses over-fetching and under-fetching problems

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[n-plus-one-query]]
- [[eager-loading]]
- [[excessive-network-calls]]
