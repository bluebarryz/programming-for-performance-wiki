---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L32
prerequisites:
  - "[[mm1-queue]]"
  - "[[kendall-notation]]"
  - "[[utilization]]"
---

# M/M/k Queue

An M/M/k queue extends the [[mm1-queue]] to k identical servers sharing a single queue. Jobs arrive at the queue and are served by the next available server.

Per-server utilization: **rho = lambda * s / k**

An intermediate value K (computational shorthand) is needed:

K = [sum from i=0 to k-1 of (lambda*s)^i / i!] / [sum from i=0 to k of (lambda*s)^i / i!]

The probability that all servers are busy (Erlang C formula):

**C = (1 - K) / (1 - lambda*s*K / k)**

Key formulas:
- **Average completion time**: T_q = C*s / (k*(1-rho)) + s
- **Average queue length**: W = C * rho / (1-rho)

**Printer example**: One printer with s=2min, lambda=0.4 gives rho=0.8 and T_q=10 minutes. Options: (1) one printer twice as fast: s=1, rho=0.4, T_q=1.67min. (2) Two printers at original speed: T_q=2.38min. Two observations: doubling printers made jobs complete nearly 4x faster, but the single fast printer wins when utilization is low.

## Prerequisites

- [[mm1-queue]] — M/M/k extends the M/M/1 model to k servers
- [[kendall-notation]] — M/M/k is described using Kendall notation
- [[utilization]] — Per-server utilization rho = lambda * s / k is central to the formulas

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[mm1-queue]]
- [[kendall-notation]]
- [[utilization]]
- [[one-fast-server-vs-many-slow]]
