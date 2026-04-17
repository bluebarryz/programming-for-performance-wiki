---
tags:
  - concept
  - ece459
  - queueing-theory
  - statistics
lectures:
  - L32
prerequisites:
  - "[[queueing-theory]]"
---

# Convergence

In the context of queueing theory, convergence means that a random variable (such as the number of jobs in a system) will settle toward an expected value given enough samples or enough sample paths. You might flip a coin four times and get all heads, but with enough flips the proportion converges to 0.5.

There may be some sample paths that never converge (e.g., perpetually heads), but these "bad paths" have a probability mass of zero -- they are infinitely unlikely. The course only considers systems where convergence holds.

Convergence is important because it justifies using measurements and averages to characterize system behavior. It means that if we get past initial conditions and take enough samples, the system will "behave well."

## Prerequisites

- [[queueing-theory]] — Convergence justifies using averages to characterize queueing system behavior

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[ergodicity]]
- [[time-average-vs-ensemble-average]]
