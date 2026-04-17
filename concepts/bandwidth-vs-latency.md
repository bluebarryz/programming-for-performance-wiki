---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites: []
---

# Bandwidth vs Latency

Performance has two fundamental metrics:

- **Bandwidth** (items per unit time): How much work gets done simultaneously. Measured in transactions per second, jobs per hour, etc. Parallelization improves bandwidth.
- **Latency** (time per item): How long a single task takes to complete. Also called response time. Especially important for user-facing tasks (Google targets low latency for DNS via 8.8.8.8; the 100ms threshold for perceived instantaneous response).

These are somewhat related -- reducing time per item from 5s to 4s increases throughput from 12 to 15 items per minute -- but they are distinct. A truck full of hard drives crossing the continent is high-bandwidth but also high-latency. The course focuses on completing items (doing useful work) rather than transmitting information, but the distinction matters.

In general, parallelism improves bandwidth but not latency.

## Prerequisites
None — foundational concept.

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[parallelism]]
- [[improving-latency]]
- [[scalability]]
