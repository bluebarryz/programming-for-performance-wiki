---
tags:
  - concept
  - ece459
  - queueing-theory
  - performance
lectures:
  - L31
prerequisites:
  - "[[queueing-theory]]"
  - "[[arrival-rate-and-service-rate]]"
---

# Load Balancing

Load balancing distributes incoming work across multiple servers (a "server farm") via a dispatcher. All servers are assumed to be identical (or close enough). The dispatcher assigns incoming tasks to one of n servers based on a [[task-assignment-policies|task assignment policy]].

There are two broad approaches:
1. **Pre-assignment**: the dispatcher assigns a job to a server when it arrives
2. **After-the-fact assignment (work-stealing)**: monitoring queues and reassigning work if it piles up somewhere

Which policy yields the lowest mean response time depends on job variability and workload characteristics. This is not fully understood -- it remains an open research question.

## Prerequisites

- [[queueing-theory]] — Load balancing is a queueing problem of distributing work across servers
- [[arrival-rate-and-service-rate]] — Understanding how arrival rate splits across servers requires these fundamentals

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]

## Related Concepts

- [[task-assignment-policies]]
- [[queueing-theory]]
- [[one-fast-server-vs-many-slow]]
