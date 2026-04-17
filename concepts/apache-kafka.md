---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[message-passing-multi-computer]]"
  - "[[parallelism]]"
---

# Apache Kafka

Apache Kafka is a distributed streaming platform with significant industry adoption as a communication mechanism between services running over a network. It uses a producer-consumer model where producers write records (data elements like an invoice) into a topic (a category of messages) and consumers read items from the topic to process them. Messages remain available for a configurable retention period and can be replayed if needed.

Kafka's core strategy is writing to an immutable log that is split into partitions. The number of partitions is chosen at topic creation time, with more partitions enabling higher parallelism. Producers write records into one of the partitions, and consumers read from each partition independently, committing their offset to track progress. This means consumers do not need to coordinate with each other and can process at their own speed.

A key advantage of this architecture is that message removal is based on expiry time rather than consumption, so there is no urgency for consumers to drain the queue. This avoids problems common in standard queues where items might be lost if taken out before being durably processed. Kafka serves as a decoupling layer between services, making it well-suited for multi-computer communication in performance-oriented distributed systems.

## Prerequisites

- [[message-passing-multi-computer]] — Kafka is a message passing platform for multi-computer systems
- [[parallelism]] — Kafka partitions enable parallel consumption of messages

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[message-passing-multi-computer]]
- [[sns-and-sqs]]
- [[rest-apis-for-distributed-systems]]
