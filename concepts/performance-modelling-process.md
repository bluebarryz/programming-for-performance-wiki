---
tags:
  - concept
  - ece459
  - queueing-theory
  - performance
lectures:
  - L32
prerequisites:
  - "[[utilization]]"
  - "[[visitation-ratio]]"
  - "[[bottleneck-device]]"
  - "[[mm1-queue]]"
---

# Performance Modelling Process

A systematic process for applying queueing theory to real system performance analysis:

1. **Convert to common time units** (typically seconds)
2. **Calculate visitation ratios** V_i -- how many times each device is used per transaction
3. **Calculate device utilization** rho_i = lambda_i * s_i
4. **Calculate CPU service time** (derived from utilization if not directly measured: s = rho / lambda)
5. **Calculate device time** V_i * S_i for each device
6. **Find the [[bottleneck-device]]** -- highest utilization
7. **Calculate maximum transaction rate** -- 1 / (S_i * V_i) for the bottleneck ([[saturation]])
8. **Calculate average transaction time** -- sum of all S_i * V_i

**Web server example**: A system serving 9,000 pages/hour with CPU, two disks, and a network interface. After filling in the table, CPU has the highest utilization (0.42), making it the bottleneck. Maximum transaction rate: 5.95 pages/second. Average transaction time: 0.474 seconds.

In practice, service times are often unknown -- only average queue sizes W are available. The [[mm1-queue]] formula W = (lambda*s)^2 / (1 - lambda*s) can be solved for s using the quadratic formula.

## Prerequisites

- [[utilization]] — Identifying the bottleneck requires calculating device utilizations
- [[visitation-ratio]] — Visitation ratios are needed to compute device time per transaction
- [[bottleneck-device]] — The modelling process centers on finding and analyzing the bottleneck
- [[mm1-queue]] — M/M/1 formulas are used to derive service times from observed queue lengths

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[bottleneck-device]]
- [[utilization]]
- [[visitation-ratio]]
- [[saturation]]
- [[mm1-queue]]
