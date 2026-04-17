---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[bandwidth-vs-latency]]"
  - "[[improving-latency]]"
---

# System Design

System design, in the context of ECE 459, refers to how the larger architecture of a software system affects the runtime performance of individual operations. The design of the system in which data lives can dominate execution time. For example, if fetching data requires multiple network calls, the overhead of those calls may dwarf the actual computation, potentially turning linear work into accidentally quadratic behaviour.

System design decisions exist at multiple levels. At the highest level is the choice between [[monolith-vs-microservices]]. At the middle level are design patterns: producer-consumer, message passing vs shared memory, pipeline architectures. At the implementation level are choices like thread pool sizes and framework configurations. Whether you can change the architecture is situation-dependent -- convincing a company to split up a five-year-old monolith is rarely feasible regardless of the performance argument.

The course identifies several common pitfalls: [[excessive-network-calls]], [[n-plus-one-query]] patterns, [[architectural-bottlenecks]], [[over-taking-responsibility]], and excessive waiting. The overarching theme is that [[complexity-and-abstraction]] is the enemy of performance -- more services and layers means more data movement, and longer communication chains are inherently slower than shorter ones.

## Prerequisites

- [[bandwidth-vs-latency]] — System design decisions affect both throughput and per-operation latency
- [[improving-latency]] — Understanding latency reduction strategies helps evaluate architectural tradeoffs

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[monolith-vs-microservices]]
- [[excessive-network-calls]]
- [[n-plus-one-query]]
- [[architectural-bottlenecks]]
- [[complexity-and-abstraction]]
- [[over-taking-responsibility]]
