---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L32
prerequisites:
  - "[[arrival-rate-and-service-rate]]"
  - "[[open-vs-closed-systems]]"
  - "[[ergodicity]]"
---

# Little's Law

Little's Law states that the average number of jobs in a system equals the product of the average arrival rate and the average time spent in the system:

**E[N] = lambda * E[T]**

where E[N] is the expected number of jobs, lambda is the arrival rate, and E[T] is the mean time in the system.

This holds regardless of the arrival process distribution (Bernoulli, Poisson, etc.), the service time distribution, or the network topology. It is remarkably general.

**Intuitive example**: A fast food restaurant has quick turnaround (low E[T]) so it needs few seats (low E[N]). A sit-down restaurant has slow turnaround (high E[T]) so it needs many seats (high E[N]).

**For closed systems**: N = X * E[T], where N is the fixed multiprogramming level and X is throughput. With think time E[Z], the expected response time becomes E[R] = N/X - E[Z].

## Prerequisites

- [[arrival-rate-and-service-rate]] — Little's Law uses arrival rate (lambda) as a key parameter
- [[open-vs-closed-systems]] — The law takes different forms for open and closed systems
- [[ergodicity]] — Little's Law assumes the system is ergodic so that averages are well-defined

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[queueing-theory]]
- [[arrival-rate-and-service-rate]]
- [[open-vs-closed-systems]]
- [[ergodicity]]
