---
tags:
  - lecture
  - ece459
  - performance
  - rate-limiting
  - external-services
lecture: 16
title: Rate Limits
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
---

# L16 - Rate Limits

When your application depends on external services, you may hit rate limits -- maximum request rates imposed by the service provider. This lecture explains why rate limits exist (cost, DoS prevention, data scraping protection), and covers strategies for dealing with them: doing less work, caching, grouping requests, patience (queuing/throttling), scheduling for off-peak times, and negotiating higher limits. It also covers handling rate-limit errors gracefully using exponential backoff with jitter.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Scalability concepts needed to understand why external services become bottlenecks

## Concepts Covered

- [[rate-limiting]]
- [[denial-of-service]]
- [[caching]]
- [[request-grouping]]
- [[request-throttling]]
- [[exponential-backoff]]
- [[jitter]]
