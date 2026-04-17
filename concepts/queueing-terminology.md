---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
prerequisites:
  - "[[queueing-theory]]"
  - "[[bandwidth-vs-latency]]"
---

# Queueing Terminology

The standard terms and mathematical symbols used in queueing theory:

| Symbol | Term | Meaning |
|--------|------|---------|
| S | Service time | Time to complete a single request |
| V | Visits | Number of visits to the server |
| D | Service demand | Total service requirement |
| R | Response time | Sum of wait time and service time for a single visit |
| R' | Residence time | Total response time across multiple visits |
| X | Throughput | Rate at which requests are completed |
| lambda | Arrival rate | Rate at which requests arrive |
| U | Utilization | Fraction of time the server is busy |
| W | Wait time | Time spent waiting in the queue |
| N | Queue length | Total number of jobs waiting and/or being served |

Additional terms:
- **Server** -- the entity fulfilling requests
- **Customer** -- the initiator of service requests
- **Service time** -- time from when a server starts serving a customer to when the next is called

## Prerequisites

- [[queueing-theory]] — These terms are the vocabulary of queueing theory
- [[bandwidth-vs-latency]] — Throughput and response time are formalized as queueing terminology symbols X and R

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]

## Related Concepts

- [[queueing-theory]]
- [[arrival-rate-and-service-rate]]
- [[utilization]]
