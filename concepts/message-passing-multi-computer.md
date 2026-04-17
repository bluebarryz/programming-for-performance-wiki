---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[parallelism]]"
  - "[[blocking-vs-non-blocking-io]]"
---

# Message Passing for Multi-Computer Systems

When scaling beyond a single machine, shared memory is no longer an option and programs must communicate via message passing. While Rust encourages message passing even within a single process, multi-computer message passing has a critical difference: communication over the network is much more expensive than communicating within the same system, so the amount of data exchanged must be carefully minimized.

The available mechanisms for multi-computer message passing range from low-level sockets to higher-level abstractions. [[rest-apis-for-distributed-systems]] provide a familiar HTTP-based approach that can be synchronous or use callbacks. [[apache-kafka]] offers a distributed streaming platform with producer-consumer semantics and topic-based message routing. AWS services like [[sns-and-sqs]] provide managed alternatives for notification and queuing. The choice of mechanism depends on requirements around latency, ordering, persistence, and coupling between services.

The same principles from single-machine concurrency apply: producer-consumer patterns, channels, and subscriptions all translate to the multi-computer setting. The key engineering challenge is managing the higher communication costs and the additional failure modes (network partitions, node crashes) that don't exist in single-machine parallelism.

## Prerequisites

- [[parallelism]] — Multi-computer message passing extends parallelism beyond a single machine
- [[blocking-vs-non-blocking-io]] — Network communication uses the same async IO patterns from L05

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[apache-kafka]]
- [[mpi]]
- [[rest-apis-for-distributed-systems]]
- [[sns-and-sqs]]
