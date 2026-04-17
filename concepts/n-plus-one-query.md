---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[excessive-network-calls]]"
  - "[[accidentally-quadratic]]"
---

# N+1 Query

The N+1 query problem is a common performance anti-pattern where fetching a list of N items results in N+1 database queries: one to get the list, then one per item to fetch related data. For example, to send payment reminders for 500 unpaid invoices, a naive implementation queries the invoice list (1 query), then looks up each customer's email individually (500 queries), totaling 501 database round-trips.

The fix when writing SQL directly is straightforward: use a JOIN to get all needed data in one query, or use a `WHERE id IN (...)` clause to batch the lookups into at most two queries. The problem is more insidious with ORMs (Object-Relational Mappings) like Hibernate or ActiveRecord, which may unintentionally generate N+1 queries from innocent-looking code. Checking the generated SQL is essential.

In [[graphql]] backends, the problem is especially tricky because the server cannot predict which queries callers will compose. The Rust crate `juniper_eager_loading` addresses this by separating the data model from the GraphQL schema and using a `HasOne` enum to batch-load related entities. The general solutions are [[eager-loading]] (pre-fetching related entities), batching (collecting IDs and querying in bulk), and caching (avoiding repeated lookups entirely).

## Prerequisites

- [[excessive-network-calls]] — N+1 queries are a specific manifestation of excessive network calls
- [[accidentally-quadratic]] — N+1 turns linear work into quadratic database round-trips

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[excessive-network-calls]]
- [[eager-loading]]
- [[graphql]]
- [[system-design]]
