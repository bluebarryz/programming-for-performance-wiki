---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[message-passing-multi-computer]]"
---

# SNS and SQS

SNS (Simple Notification Service) and SQS (Simple Queueing Service) are AWS-based messaging services used for decoupling communication between distributed programs. They serve different purposes and have distinct characteristics.

SNS is designed for sending messages to multiple receivers simultaneously. Use cases include push notifications, broadcasting record updates to all systems, and sending pager alerts when things go wrong. SNS messages are not persistent: if a subscriber is not available when the message is sent, the message is lost. This makes SNS suitable for time-sensitive notifications where missing a message is acceptable.

SQS is designed for work queues where items will be consumed by worker processes. It is suited for batch processing that is not particularly time-sensitive. SQS messages are deleted after being consumed, and the service may or may not provide ordering guarantees depending on the queue type. SQS has limits on message retention time. Both services serve as alternatives to [[apache-kafka]] for multi-computer communication, with the tradeoff of being tied to the AWS ecosystem in exchange for managed infrastructure and simpler operational overhead.

## Prerequisites

- [[message-passing-multi-computer]] — SNS and SQS are managed messaging services for multi-computer communication

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[apache-kafka]]
- [[message-passing-multi-computer]]
- [[rest-apis-for-distributed-systems]]
- [[cloud-computing]]
