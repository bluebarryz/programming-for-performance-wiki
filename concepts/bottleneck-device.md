---
tags:
  - concept
  - ece459
  - queueing-theory
  - performance
lectures:
  - L31
  - L32
prerequisites:
  - "[[utilization]]"
  - "[[amdahls-law]]"
---

# Bottleneck Device

The bottleneck device is the component in a system that limits maximum throughput. It is the device with the highest [[utilization]] (rho).

In the [[performance-modelling-process]], once device utilizations are calculated, the bottleneck is identified as the device with the largest rho. The maximum transaction rate the system can handle is 1 / (S_i * V_i) for the bottleneck device i. This is also called [[saturation]].

Improving the bottleneck device improves overall system performance. Improving non-bottleneck devices typically has little or no effect. In a closed system example from L31, replacing one of two servers with a faster one had negligible effect because the other server remained the bottleneck.

This is analogous to Amdahl's Law: the slowest component limits the overall speedup.

## Prerequisites

- [[utilization]] — The bottleneck is the device with the highest utilization
- [[amdahls-law]] — Bottleneck analysis is analogous to Amdahl's Law: the slowest component limits overall speedup

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]
- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[utilization]]
- [[performance-modelling-process]]
- [[saturation]]
- [[open-vs-closed-systems]]
