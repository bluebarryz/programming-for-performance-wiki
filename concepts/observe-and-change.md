---
tags:
  - concept
  - ece459
  - runtime-optimization
lectures:
  - L20
prerequisites:
  - "[[caching]]"
  - "[[plan-caching]]"
---

# Observe and Change

Observe and change is a self-optimization strategy where a program's configuration or behavior adapts at runtime based on observed performance. If there are multiple routes to the same outcome, the program measures which route is best and switches to it. This is effective both because the initial guess may be wrong and because conditions can change at any time.

A concrete example is database query processing: the server creates an execution plan based on estimated costs, but could later try a different strategy, observe that it is faster, and switch. Since many queries are repeated or similar, remembering what worked is valuable. Another example is data organization: sorting a data structure by the attribute used most frequently for lookups, and re-sorting when usage patterns change. The same principle applies to external services -- if there are multiple servers to send requests to, the program can measure response times, primarily use the fastest server, but periodically probe the others to detect when conditions change.

This strategy sits between simple caching (which changes what is in memory but is relatively trivial) and more advanced techniques like [[binary-rewriting]] or [[jit-compilation]] (which change the code itself). Observe and change is practical and widely applicable: it requires only that the program have configurable parameters and a way to measure the effect of different choices.

## Prerequisites

- [[caching]] — Caching is the simplest form of runtime adaptation; observe-and-change goes further
- [[plan-caching]] — Database plan caching is a concrete example of the observe-and-change strategy

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[genetic-algorithms]]
- [[plan-caching]]
- [[jit-compilation]]
- [[binary-rewriting]]
