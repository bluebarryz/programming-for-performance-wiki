---
tags:
  - concept
  - ece459
  - queueing-theory
  - statistics
lectures:
  - L32
prerequisites:
  - "[[time-average-vs-ensemble-average]]"
  - "[[convergence]]"
---

# Ergodicity

A system is ergodic if the time average and ensemble average are the same. An ergodic system must satisfy three properties:

1. **Irreducibility**: The process can get from any state to any other state. The initial state does not matter -- starting at 0 jobs or 10 jobs, the system can still reach any state.

2. **Positive recurrence**: Given irreducibility, any state i is revisited infinitely often, and the expected time between visits is finite. In a queue, this means the "empty queue" state acts as a natural restart point.

3. **Aperiodicity**: The state of the system is not related to the time. If the system is always in state 0 at even times and state 1 at odd times, the ensemble average would depend on when you sample, which breaks the equivalence.

Ergodicity is what makes Tim's single long run equivalent to Enzo's many independent runs. Every time the queue empties, it is a "renewal" or "restart" -- so a single long run is really just a chain of independent shorter runs.

## Prerequisites

- [[time-average-vs-ensemble-average]] — Ergodicity is the property that makes time and ensemble averages equivalent
- [[convergence]] — Ergodicity builds on the assumption that system measurements converge

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[time-average-vs-ensemble-average]]
- [[convergence]]
- [[littles-law]]
