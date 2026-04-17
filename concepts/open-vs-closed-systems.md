---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
  - L32
prerequisites:
  - "[[arrival-rate-and-service-rate]]"
  - "[[queueing-theory]]"
---

# Open vs. Closed Systems

An **open system** is one where arrivals are independent of the system's state -- jobs arrive from outside at some rate lambda regardless of how many jobs are currently in the system.

A **closed system** has a fixed number of jobs N (the multiprogramming level, or MPL). As soon as one job completes, a new one enters. Batch processing systems are a classic example.

Key differences:
- In an open system, throughput is limited by the arrival rate (since lambda < mu). Increasing mu raises maximum possible throughput but not actual throughput if there is no more work.
- In a closed system, the system always runs at capacity, so throughput equals the service rate mu. Increasing mu directly increases throughput.
- Closed systems can behave counterintuitively. For example, replacing one server with a faster one in a closed system with N=6 jobs split between two servers may have negligible effect because the [[bottleneck-device]] is the limiting factor.

For closed systems, [[littles-law]] becomes N = X * E[T], where X is throughput. With think time E[Z], the expected response time is E[R] = N/X - E[Z].

**Measuring mu** differs between the two: in an open system, ramp up lambda until the completion rate levels off. In a closed system, set think time to zero and measure completions per second directly.

## Prerequisites

- [[arrival-rate-and-service-rate]] — Open vs closed systems differ in how arrival rate relates to throughput
- [[queueing-theory]] — System type classification is part of the queueing framework

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]
- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[arrival-rate-and-service-rate]]
- [[littles-law]]
- [[bottleneck-device]]
- [[measuring-service-rate]]
