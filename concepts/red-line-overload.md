---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
prerequisites:
  - "[[arrival-rate-and-service-rate]]"
---

# Red Line Overload

Red line overload occurs when the arrival rate lambda exceeds the service rate mu. In this situation, the expected number of jobs in the system grows without bound:

E[N(t)] = E[A(t)] - E[D(t)] >= t(lambda - mu)

As t approaches infinity, if lambda > mu, the queue length goes to infinity. The system can never catch up.

While lambda and mu are averages (so temporary imbalances are fine), in the long term the system must have lambda < mu to remain stable.

All queueing theory analysis assumes the system is not overloaded (lambda < mu). If this assumption is violated, the models break down.

## Prerequisites

- [[arrival-rate-and-service-rate]] — Overload occurs when arrival rate exceeds service rate (lambda > mu)

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]

## Related Concepts

- [[arrival-rate-and-service-rate]]
- [[queueing-theory]]
- [[saturation]]
