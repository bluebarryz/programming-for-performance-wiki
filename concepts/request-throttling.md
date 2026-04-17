---
tags:
  - concept
  - ece459
  - performance
  - external-services
lectures:
  - L16
prerequisites:
  - "[[rate-limiting]]"
---

# Request Throttling

Request throttling (patience/queuing) is the strategy of distributing requests over more time to stay under a rate limit. Requests are added to a queue and processed at a controlled rate as they reach the front.

If all outgoing requests go through the queue, simply controlling the dequeue rate is sufficient to respect the rate limit. The queue also provides a central place to adjust the rate if the limit changes.

In Rust, the `ratelimit` crate provides token-bucket-based rate limiters. Examples include steady-rate limiters (e.g., 1 token/second with no burst) and burst-capable limiters (e.g., 1000 tokens/hour with all tokens available for a single burst).

## Trade-offs

- Queuing converts a synchronous flow into an asynchronous one, which may not suit user-interactive applications
- Delayed is better than denied -- a throttled request eventually succeeds, a rejected one does not
- For non-urgent requests, scheduling them for off-peak times is another form of throttling

## Prerequisites

- [[rate-limiting]] — Throttling is a strategy for respecting rate limits by controlling dequeue rate

## Lectures

- [[L16-Rate-Limits]]

## Related Concepts

- [[rate-limiting]]
- [[request-grouping]]
- [[exponential-backoff]]
