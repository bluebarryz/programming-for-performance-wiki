---
tags:
  - concept
  - ece459
  - queueing-theory
  - statistics
lectures:
  - L32
prerequisites:
  - "[[convergence]]"
  - "[[queueing-theory]]"
---

# Time Average vs. Ensemble Average

Two different approaches to measuring system behaviour, illustrated by "Tim and Enzo":

**Time average (Tim's approach)**: Run one very long simulation, take many samples throughout, and average them. The risk is that a single unusual run could skew results.

**Ensemble average (Enzo's approach)**: Run many shorter independent simulations, sample each one after it has reached steady state, and average those samples. This better captures the system at "steady state" and allows for parallel execution and confidence intervals.

Both approaches require handling initial conditions: Enzo must wait for startup effects to attenuate before sampling, and Tim must ensure initial conditions affect only a small portion of measurements.

For [[ergodicity|ergodic]] systems, both approaches yield the same result. The key insight is that in an ergodic system, a single long run is equivalent to many independent runs because every time the system returns to a "restart" state (e.g., empty queue), it is like beginning a new independent run.

**Time average formula**: lim(t->inf) [sum of T_i for i=1 to A(t)] / A(t)

**Ensemble average formula**: lim(t->inf) E[T_i]

## Prerequisites

- [[convergence]] — Both averaging approaches require that the system converges to meaningful values
- [[queueing-theory]] — These measurement approaches are used to characterize queueing system behavior

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[convergence]]
- [[ergodicity]]
