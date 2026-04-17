---
tags:
  - concept
  - ece459
  - performance
  - retry-strategy
lectures:
  - L16
prerequisites:
  - "[[exponential-backoff]]"
---

# Jitter

Jitter is an improvement to [[exponential-backoff]] that adds a small random component to the retry delay. Without jitter, if two threads fail at time X, they will both retry at exactly time X + delay, fight over the same resource, fail again, and retry at X + 2*delay, and so on indefinitely.

By adding randomness (e.g., one thread retries at X + 9, another at X + 7), the retries are spread out and collisions are avoided.

Exponential backoff with jitter is well-suited for scenarios with many independent clients accessing the same resource. For a single client accessing a resource repeatedly, something resembling TCP congestion control may be more appropriate.

## Prerequisites

- [[exponential-backoff]] — Jitter is an improvement to exponential backoff that adds randomness to retry delays

## Lectures

- [[L16-Rate-Limits]]

## Related Concepts

- [[exponential-backoff]]
- [[rate-limiting]]
