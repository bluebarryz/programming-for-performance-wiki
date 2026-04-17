---
tags:
  - concept
  - ece459
  - devops
  - operations
lectures:
  - L35
prerequisites:
  - "[[devops]]"
  - "[[kubernetes]]"
---

# Health Checks

Health checks are automated tests that verify an application is running and able to respond to requests. Basic health checks simply confirm the app is up, but more realistic checks verify that the system can do useful work -- such as reaching its database or completing basic user workflows like logging in and viewing data.

A simple health check that only verifies connectivity will not reveal performance problems. The app might be reachable and the database accessible, but if response times are ten times slower than usual, that is a serious issue. Comprehensive health monitoring should also look at CPU load, memory utilization, disk space, disk I/O, network traffic, clock skew, queue lengths, and application response times.

Health checks tie into the broader [[monitoring-and-alerting]] system. With multiple systems, a dashboard that summarizes health status across all services is essential. The dashboard should be detailed enough to detect problems but not so overwhelming that it becomes a wall of data. Tools like [[kubernetes]] can use health checks to automatically replace unhealthy instances.

## Prerequisites

- [[devops]] — Health checks are a basic operational practice in DevOps
- [[kubernetes]] — Kubernetes uses health checks to automatically replace unhealthy instances

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[monitoring-and-alerting]]
- [[kubernetes]]
- [[devops]]
