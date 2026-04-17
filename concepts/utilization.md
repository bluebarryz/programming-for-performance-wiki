---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
  - L32
prerequisites:
  - "[[arrival-rate-and-service-rate]]"
  - "[[queueing-terminology]]"
---

# Utilization

Utilization (rho) is the fraction of time a server is busy, expressed as a value between 0 and 1. It is calculated as:

**rho = lambda x s**

where lambda is the arrival rate and s is the service time.

For an M/M/k system with k servers, the per-server utilization is rho = lambda * s / k.

Utilization is critical for understanding system performance because queueing delays grow nonlinearly as utilization approaches 1. In the [[mm1-queue]] model, the average number of jobs in the system is rho / (1 - rho), which explodes as rho approaches 1.

In the [[performance-modelling-process]], the device with the highest utilization is the [[bottleneck-device]] that limits maximum throughput.

## Prerequisites

- [[arrival-rate-and-service-rate]] — Utilization is computed directly from arrival rate and service time (rho = lambda * s)
- [[queueing-terminology]] — Utilization (U/rho) is one of the core queueing symbols

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]
- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[arrival-rate-and-service-rate]]
- [[mm1-queue]]
- [[mmk-queue]]
- [[bottleneck-device]]
- [[performance-modelling-process]]
