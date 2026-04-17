---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[scalability]]"
  - "[[amdahls-law]]"
---

# Scalability Cost

Scalability cost refers to the overhead introduced by scaling a system to multiple machines, which can be substantial enough to negate the benefits of additional compute resources. The paper "Scalability! But at what COST?" (McSherry et al.) formalized this concern by showing that 128-core distributed systems sometimes failed to outperform a single laptop running a competent implementation.

The overhead comes from multiple sources: network communication between nodes, serialization and deserialization of data, coordination and synchronization protocols, fault tolerance mechanisms, and the complexity of the distributed framework itself. These costs mean that the important metric is not relative scalability (does adding more nodes make it faster?) but absolute performance (how fast does it actually solve the problem?). A system that scales linearly from 1000 seconds to 500 seconds with double the hardware is still worse than a laptop that solves it in 300 seconds.

The practical lesson is to avoid scaling up to n systems merely to deal with the complexity of scaling up to n systems. Or as Oscar Wilde put it: "The bureaucracy is expanding to meet the needs of the expanding bureaucracy." Before adopting a distributed architecture, verify that it genuinely outperforms a well-optimized single-machine solution for your specific workload.

## Prerequisites

- [[scalability]] — Understanding scalability is required to appreciate the costs of scaling
- [[amdahls-law]] — Amdahl's law predicts diminishing returns from adding more parallel resources

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[clusters-vs-laptops]]
- [[cloud-computing]]
- [[scalability]]
