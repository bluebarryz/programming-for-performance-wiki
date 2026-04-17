---
tags:
  - concept
  - ece459
  - queueing-theory
  - probability
lectures:
  - L32
prerequisites:
  - "[[queueing-theory]]"
  - "[[kendall-notation]]"
---

# Markov Process

A Markov process is a memoryless stochastic process where the future state depends only on the present state, not on past history. It is one of three probabilistic process models used in queueing theory:

1. **Deterministic (D)** -- constant, predictable inter-arrival and service times
2. **Markov (M)** -- memoryless; future independent of past
3. **General (G)** -- completely arbitrary

For Markov processes:
- Number of arrivals follows the **Poisson distribution**
- Inter-arrival times follow the **exponential distribution**
- Service times follow the **exponential distribution**

The "M" in [[kendall-notation]] (e.g., M/M/1, M/M/k) stands for Markov. The course focuses on Markov processes because they are mathematically tractable and produce clean formulas for queue metrics.

## Prerequisites

- [[queueing-theory]] — Markov processes provide the probabilistic foundation for queueing models
- [[kendall-notation]] — The "M" in Kendall notation stands for Markov

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[kendall-notation]]
- [[mm1-queue]]
- [[mmk-queue]]
