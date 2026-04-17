---
tags:
  - concept
  - ece459
  - security
  - performance
lectures:
  - L16
prerequisites: []
---

# Denial of Service (DoS/DDoS)

A Denial-of-Service (DoS) attack negatively impacts a service's functioning by flooding it with invalid requests. When the attack comes from numerous clients, it becomes a Distributed Denial of Service (DDoS) attack, which prevents simple countermeasures like blocking a single IP.

Enough invalid requests can overwhelm a service, causing it to crash, exhaust resources (e.g., network handles), or become unusably slow. Rate limits are one defense mechanism against such attacks, though they exist for broader reasons than just security.

## Prerequisites

None — foundational concept.

## Lectures

- [[L16-Rate-Limits]]

## Related Concepts

- [[rate-limiting]]
