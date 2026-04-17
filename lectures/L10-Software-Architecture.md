---
tags:
  - lecture
  - ece459
  - architecture
  - system-design
  - performance
lecture: 10
title: Software Architecture
date: 2025-07-07
prerequisite_lectures:
  - "[[L05-Asynchronous-IO]]"
  - "[[L09-Algorithms-Concurrency-and-Parallelism]]"
---

# L10 - Software Architecture

This lecture examines how software architecture decisions affect performance. It covers choosing between monolith and microservices architectures, the danger of unnecessary complexity and over-abstraction, and several specific performance pitfalls: excessive network calls, the N+1 query problem, architectural bottlenecks/chokepoints, over-taking responsibility, and too much waiting. Solutions include JWTs for distributed auth, eager loading, GraphQL, async I/O, and message passing to reduce lock contention.

## Prerequisite Lectures
- [[L05-Asynchronous-IO]] — Async I/O patterns referenced as solutions to waiting problems
- [[L09-Algorithms-Concurrency-and-Parallelism]] — Concurrency and lock contention concepts applied at the architecture level

## Concepts Covered

- [[system-design]]
- [[monolith-vs-microservices]]
- [[complexity-and-abstraction]]
- [[excessive-network-calls]]
- [[n-plus-one-query]]
- [[architectural-bottlenecks]]
- [[over-taking-responsibility]]
- [[async-io-and-waiting]]
- [[graphql]]
- [[eager-loading]]
- [[lock-contention]]
