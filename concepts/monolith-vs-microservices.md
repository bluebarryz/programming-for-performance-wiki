---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[system-design]]"
---

# Monolith vs Microservices

A monolith architecture is a single deployable unit containing all functionality. Communication between parts is in-memory or via internal APIs, with no network overhead. A microservices architecture splits functionality into many independently deployable units that communicate over the network. Most medium-to-large companies use a mixture of both approaches.

From a performance perspective, monoliths have the advantage of avoiding network communication overhead between components. Microservices introduce latency for every inter-service call, including connection establishment, authentication, serialization, and unpacking. However, microservices offer the ability to scale individual components independently and to deploy changes to one service without redeploying the entire system.

The course's general advice is to start with a monolith and only break off microservices when there is demonstrated value in doing so. The industry has cycled through monoliths being standard, microservices coming into vogue, and then a backlash against microservices. Most high-level architecture decisions like this are not made primarily with performance in mind, but understanding the performance tradeoffs is important. Worries about excessive network calls are a legitimate drawback of microservices, though never the sole criterion for the decision.

## Prerequisites

- [[system-design]] — Monolith vs microservices is the highest-level system design decision

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[system-design]]
- [[excessive-network-calls]]
- [[architectural-bottlenecks]]
- [[complexity-and-abstraction]]
