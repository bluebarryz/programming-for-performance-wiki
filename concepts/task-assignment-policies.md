---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
prerequisites:
  - "[[load-balancing]]"
  - "[[queueing-theory]]"
---

# Task Assignment Policies

Task assignment policies determine how a [[load-balancing|load balancer]] distributes jobs to servers:

- **Random** -- assign to a random server
- **Round-Robin** -- the i-th job goes to server (i mod n)
- **Shortest-Queue** -- assign to the server with the fewest queued jobs
- **Size-Interval-Task-Assignment** -- route short jobs to one server, medium to another, long to another
- **Least-Work-Left** -- assign to the server with the least total remaining work (sum of job sizes)
- **Central-Queue** -- instead of pushing to servers, idle servers pull from a shared queue

Which policy yields the lowest mean response time is not fully known -- it depends on job variability and workload characteristics. This remains an open research question.

## Prerequisites

- [[load-balancing]] — Task assignment policies are the strategies a load balancer uses to distribute work
- [[queueing-theory]] — Evaluating policies requires queueing theory to analyze mean response times

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]

## Related Concepts

- [[load-balancing]]
- [[queueing-theory]]
