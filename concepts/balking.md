---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[queueing-theory]]"
  - "[[arrival-rate-and-service-rate]]"
---

# Balking

Balking is what happens when a customer looks at a queue, decides it is too long, and chooses not to enter it at all. In the food hall example, if the line for tacos is extremely long, you might walk away without joining. At Service Ontario, if there is a long line out the door, you might decide not to bother and come back another time.

In both cases, there is an implicit or explicit estimation of the waiting time. The customer assesses the queue length, perhaps estimates the service time, and concludes that the expected wait exceeds their willingness to wait. Some establishments put out signs indicating the expected waiting time from a given point, which helps customers make this decision.

Balking is one of three behaviors (alongside [[reneging]] and [[loss-systems]]) that complicate simple queueing models. In real systems, balking means that not all arriving customers actually enter the queue, which affects arrival rate calculations and system throughput.

## Prerequisites

- [[queueing-theory]] — Balking complicates basic queueing models by reducing effective arrival rate
- [[arrival-rate-and-service-rate]] — Balking means not all arrivals enter the queue, affecting arrival rate calculations

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[reneging]]
- [[loss-systems]]
- [[virtual-queues]]
