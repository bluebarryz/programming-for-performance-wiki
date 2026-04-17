---
tags:
  - concept
  - ece459
  - performance
  - retry-strategy
lectures:
  - L16
prerequisites:
  - "[[rate-limiting]]"
---

# Exponential Backoff

Exponential backoff is a retry strategy for handling rejected or failed requests. After a failure, wait a short time and retry. If it fails again, wait a multiplicatively longer time before the next retry. Continue until success or a maximum retry count is reached.

This applies beyond rate limiting -- if a resource is down for maintenance, hammering it every second wastes effort and can worsen overload. The exponentially increasing delay gives the service time to recover.

Some APIs include a "Retry-After" header in rate-limit responses, in which case you should respect that value instead.

## Prerequisites

- [[rate-limiting]] — Exponential backoff is the retry strategy when rate-limited requests are rejected

## Lectures

- [[L16-Rate-Limits]]

## Related Concepts

- [[rate-limiting]]
- [[jitter]]
- [[request-throttling]]
