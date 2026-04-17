---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[message-passing-multi-computer]]"
  - "[[callbacks]]"
---

# REST APIs for Distributed Systems

REST (Representational State Transfer) APIs over HTTP provide a reasonable level of abstraction for multi-computer communication. In ECE 459, students have already encountered asynchronous I/O using HTTP via curl, and these same mechanisms can be used for inter-service communication in distributed systems.

REST APIs are often completely synchronous (request-response), but they can be extended with asynchronous patterns: callbacks to be notified when a computation completes, or polling where the caller checks back later to see if a request is finished. However, these are not truly asynchronous because the remote machine must be available at the time of each call. This tight coupling means that if the remote service is down, the caller is blocked or must handle the failure.

For more decoupled communication, message-based systems like [[apache-kafka]] or [[sns-and-sqs]] are preferred. REST APIs remain a good choice when the communication pattern is naturally request-response, when the overhead of a message broker is not justified, or when interoperability with existing HTTP-based infrastructure is important.

## Prerequisites

- [[message-passing-multi-computer]] — REST APIs are one mechanism for multi-computer message passing
- [[callbacks]] — REST APIs can use callbacks for asynchronous notification

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[message-passing-multi-computer]]
- [[apache-kafka]]
- [[sns-and-sqs]]
