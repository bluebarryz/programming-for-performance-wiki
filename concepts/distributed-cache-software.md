---
tags:
  - concept
  - ece459
  - cache
lectures:
  - "08"
prerequisites:
  - "[[mesi-protocol]]"
  - "[[invalidation-vs-update]]"
  - "[[cache-coherency]]"
---

# Distributed Cache (Software)

The cache coherency protocols used in CPU hardware (such as [[mesi-protocol]]) can also be applied to distributed software caches like Redis. In a software distributed cache, multiple nodes each hold cached copies of data retrieved from a database, and the same coherency problems arise: when one node updates a cached item, the other nodes' copies may become stale.

The lecture presents a pseudocode implementation of a distributed software cache using MESI states with write-back behaviour. Key operations include: Get Item (check local cache, then ask other nodes, then fall back to the database), Update Item (transition to Modified state and send invalidation messages to other nodes), and handling node joins and departures (writing back Modified items to the database before leaving).

The advantage of the software scenario is that the developer gets to choose the coherency configuration. With CPU caches, you get whatever the hardware designers provided. In software, you can choose between invalidation and update strategies, configure consistency levels, and decide how aggressively to cache based on the application's tolerance for stale data. This makes understanding the underlying protocols valuable for designing high-performance distributed systems.

## Prerequisites

- [[mesi-protocol]] — The software implementation uses MESI states and write-back behaviour
- [[invalidation-vs-update]] — The software cache must choose between invalidation and update strategies
- [[cache-coherency]] — The software cache solves the same coherency problem as hardware caches

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[cache-coherency]]
- [[mesi-protocol]]
- [[invalidation-vs-update]]
- [[write-back-cache]]
