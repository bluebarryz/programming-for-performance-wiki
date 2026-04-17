---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[n-plus-one-query]]"
---

# Eager Loading

Eager loading is a strategy for avoiding the [[n-plus-one-query]] problem by fetching related entities alongside the primary entities in advance, even if the related data might not be needed. Instead of issuing a separate query for each related record, eager loading batches the lookups into fewer, larger queries.

In the context of ORMs (Object-Relational Mappings) like Hibernate or Rails ActiveRecord, eager loading can be configured to pre-fetch associations. For example, when loading users who each have a country, eager loading retrieves all relevant countries in a single `WHERE id IN (?, ?, ?)` query rather than issuing one query per user. Some ORMs support this natively; others require the developer to write custom SQL.

The Rust crate `juniper_eager_loading` demonstrates this pattern for GraphQL backends. It separates the GraphQL model from the underlying data structures using a `HasOne` enum with `Loaded` and `NotLoaded` variants. The resolver first loads all users, collects the distinct country IDs, queries all needed countries in one batch, and then matches them up. This approach is slightly more code, but dramatically reduces database round-trips from N+1 to 2.

## Prerequisites

- [[n-plus-one-query]] — Eager loading is the primary solution to the N+1 query problem

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[n-plus-one-query]]
- [[excessive-network-calls]]
- [[graphql]]
