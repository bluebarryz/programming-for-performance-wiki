---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[monolith-vs-microservices]]"
  - "[[system-design]]"
---

# Architectural Bottlenecks

Architectural bottlenecks (or chokepoints) arise when the system design causes repeated access to the same data or the same service, creating a point of contention that limits throughput. A common example in microservices architectures is an authorization service that must check credentials on every internal API call. The communication overhead and CPU load of cryptographic validation can overload that service and slow the entire system.

The general solution is to distribute the work so that the chokepoint is eliminated. For the authorization example, this means enabling each service to validate credentials locally -- for instance, using JWTs (JSON Web Tokens) signed with public-private key cryptography. The receiving service can verify the token without contacting the authorization service, similar to how a border agent validates a passport without calling the issuing country.

When evaluating whether a component is a bottleneck, it is worth asking whether it is over-taking responsibility or whether distributing its work would put logic where it does not belong. The answer depends on context, but the performance cost of the chokepoint must be weighed against the architectural cleanliness of centralizing the responsibility.

## Prerequisites

- [[monolith-vs-microservices]] — Bottlenecks often arise at shared services in microservices architectures
- [[system-design]] — Architectural bottlenecks are a system-level performance concern

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[system-design]]
- [[excessive-network-calls]]
- [[over-taking-responsibility]]
- [[monolith-vs-microservices]]
