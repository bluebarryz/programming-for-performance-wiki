---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L32
prerequisites:
  - "[[queueing-terminology]]"
  - "[[utilization]]"
---

# Visitation Ratio

The visitation ratio V_i is the number of times a device i is used per transaction. It is calculated by dividing the total device accesses by the number of transactions.

The CPU's visitation ratio is the sum of all other devices' visitation ratios. This is because every device operation (e.g., a disk read) involves a return to the CPU to process the result.

The product V_i * S_i gives the total "device time" per transaction for device i. This is used in the [[performance-modelling-process]] to identify the [[bottleneck-device]] and calculate the maximum transaction rate and average transaction time.

## Prerequisites

- [[queueing-terminology]] — Visitation ratio V is one of the queueing terminology symbols
- [[utilization]] — Visitation ratios are used to calculate per-device utilization

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[performance-modelling-process]]
- [[bottleneck-device]]
- [[utilization]]
