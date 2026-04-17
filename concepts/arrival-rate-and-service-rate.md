---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
  - L32
prerequisites:
  - "[[queueing-theory]]"
  - "[[queueing-terminology]]"
---

# Arrival Rate and Service Rate

The **arrival rate** (lambda) is the rate at which customers/jobs arrive at the system. The **service rate** (mu) is the rate at which the server can complete jobs. The mean job size E[S] is 1/mu.

A fundamental requirement for a stable queue is that lambda < mu (arrival rate less than service rate). If arrivals exceed departures, the expected number of jobs in the system E[N(t)] >= t(lambda - mu), which goes to infinity as t goes to infinity. This is the [[red-line-overload]] condition.

An important subtlety: raising mu (the service rate) increases the *maximum possible* throughput but does not necessarily increase *actual* throughput in an open system, because the limiting factor on completed work is arriving work. In a [[open-vs-closed-systems|closed system]], however, mu directly controls throughput since there is always work available.

## Prerequisites

- [[queueing-theory]] — Arrival and service rates are the fundamental parameters of queueing models
- [[queueing-terminology]] — Defines the symbols lambda, mu, and related terms used here

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]
- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[queueing-terminology]]
- [[utilization]]
- [[red-line-overload]]
- [[open-vs-closed-systems]]
