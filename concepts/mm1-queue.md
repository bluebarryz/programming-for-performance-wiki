---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L32
prerequisites:
  - "[[kendall-notation]]"
  - "[[utilization]]"
  - "[[markov-process]]"
---

# M/M/1 Queue

An M/M/1 queue has Markov (Poisson) arrivals, exponential service times, and a single server. It is the simplest and most commonly analyzed queueing model.

Key formulas (where rho = lambda * s):

- **Average completion time**: T_q = s / (1 - rho)
- **Average queue length** (waiting only): W = rho^2 / (1 - rho)
- **Average waiting time** (excluding service): T'_q = s*rho / (1 - rho)
- **Average number of jobs in system** (waiting + being served): rho / (1 - rho)
- **Probability of exactly x jobs**: (1 - rho) * rho^x
- **Probability of <= n jobs**: sum from i=0 to n of (1 - rho) * rho^i
- **Probability of > n jobs**: 1 - sum from i=0 to n of (1 - rho) * rho^i

**Example**: A server completes requests in 10ms on average (s=0.01s). Over 30 minutes, 117,000 jobs arrive (lambda=65/s). So rho = 0.65. Average completion time = 0.01/(1-0.65) = 28.6ms. Average queue length = 0.65^2/(1-0.65) = 1.21.

When [[performance-modelling-process|applying queueing theory to performance modelling]], service times can be derived from observed queue lengths using the quadratic formula: s = (-w +/- sqrt(w^2 + 4w)) / (2*lambda).

## Prerequisites

- [[kendall-notation]] — M/M/1 is described using Kendall notation (Markov arrivals, Markov service, 1 server)
- [[utilization]] — All M/M/1 formulas are expressed in terms of utilization rho
- [[markov-process]] — The "M" in M/M/1 denotes Markov (memoryless) processes

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[kendall-notation]]
- [[utilization]]
- [[mmk-queue]]
- [[markov-process]]
- [[performance-modelling-process]]
