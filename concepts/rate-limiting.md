---
tags:
  - concept
  - ece459
  - performance
  - external-services
lectures:
  - L16
prerequisites:
  - "[[scalability]]"
  - "[[async-io-and-waiting]]"
---

# Rate Limiting

A rate limit is the maximum rate at which a requester can make requests to a service. Requests above the limit are rejected, typically with HTTP 429 (Too Many Requests).

Rate limits can be more complex than a single threshold -- they may be segmented by request type, have multiple tiers (per hour, per day), or involve responses beyond simple rejection (delays, deprioritization).

## Why Rate Limits Exist

Every request has a cost -- CPU time, monetary cost, or opportunity cost from delaying other requests. Rate limits protect services from:

- Overload from legitimate heavy usage
- [[denial-of-service]] attacks
- Data scraping (e.g., the Parler incident where lack of rate limiting allowed trivial bulk data extraction)
- Per-request cost abuse (e.g., Unity's proposed per-install pricing)

## Strategies for Dealing with Rate Limits

1. **Do less work** -- eliminate redundant API calls discovered through code review
2. **[[caching]]** -- remember previous responses, use TTL-based expiry where domain knowledge allows
3. **[[request-grouping]]** -- batch multiple operations into a single API call
4. **[[request-throttling]]** -- queue requests and control the rate they leave the queue (e.g., using the `ratelimit` Rust crate)
5. **Schedule off-peak** -- shift non-urgent work to times when usage is low
6. **Negotiate** -- upgrade billing tier or negotiate directly with the provider

When rate limiting does occur, use [[exponential-backoff]] with [[jitter]] to retry.

## Prerequisites

- [[scalability]] — Rate limits are a constraint on scaling requests to external services
- [[async-io-and-waiting]] — Throttling and queuing strategies convert synchronous flows into asynchronous ones

## Lectures

- [[L16-Rate-Limits]]

## Related Concepts

- [[denial-of-service]]
- [[caching]]
- [[request-grouping]]
- [[request-throttling]]
- [[exponential-backoff]]
- [[jitter]]
