---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L32
prerequisites:
  - "[[bottleneck-device]]"
  - "[[utilization]]"
  - "[[red-line-overload]]"
---

# Saturation

Saturation is the maximum transaction rate a system can handle, determined by the [[bottleneck-device]]. It is calculated as:

**Maximum transaction rate = 1 / (S_i * V_i)**

for the bottleneck device i (the one with the highest [[utilization]]).

If the arrival rate lambda exceeds this saturation point, the system cannot keep up with incoming requests and enters [[red-line-overload]].

## Prerequisites

- [[bottleneck-device]] — Saturation is the maximum rate determined by the bottleneck device
- [[utilization]] — Saturation occurs when the bottleneck device reaches full utilization
- [[red-line-overload]] — Exceeding the saturation point leads to overload

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[bottleneck-device]]
- [[performance-modelling-process]]
- [[red-line-overload]]
- [[utilization]]
