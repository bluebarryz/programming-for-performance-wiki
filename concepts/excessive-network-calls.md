---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[monolith-vs-microservices]]"
  - "[[blocking-vs-non-blocking-io]]"
---

# Excessive Network Calls

Excessive network calls are a major performance pitfall in software architecture. Network communication is slow and comes with unpredictable delays. Each call carries overhead for connection establishment, authentication/token validation, and request unpacking before the actual work begins. Consequently, many small requests are generally slower than one larger request, though this may be partially offset by parallelization in async I/O scenarios.

The converse is also problematic: fetching far more data than needed (e.g., requesting an entire database table and filtering in application memory) wastes bandwidth and time. The optimal approach is to request exactly the data needed in as few calls as possible. This concern is frequently raised as an argument against microservices architectures, since internal service-to-service communication adds network overhead that a monolith avoids entirely.

The [[n-plus-one-query]] problem is a common manifestation of excessive network calls. Solutions include using JOIN queries or WHERE IN clauses to batch lookups, employing [[eager-loading]] strategies in ORMs, and caching to avoid repeated fetches of the same data.

## Prerequisites

- [[monolith-vs-microservices]] — Excessive network calls are a key drawback of microservices architectures
- [[blocking-vs-non-blocking-io]] — Understanding blocking I/O explains why many small network calls are slow

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[n-plus-one-query]]
- [[eager-loading]]
- [[monolith-vs-microservices]]
- [[architectural-bottlenecks]]
- [[system-design]]
