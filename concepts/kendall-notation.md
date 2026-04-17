---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L32
prerequisites:
  - "[[queueing-theory]]"
  - "[[arrival-rate-and-service-rate]]"
---

# Kendall Notation

Kendall notation describes queueing systems with six symbols separated by slashes: **alpha/sigma/m/beta/N/Q**

| Symbol | Meaning |
|--------|---------|
| alpha | Arrival process distribution (M=Markov, G=General, D=Deterministic) |
| sigma | Service time distribution |
| m | Number of servers |
| beta | Buffer size |
| N | Allowed population size (finite or infinite) |
| Q | Queueing policy |

The last three are often omitted, defaulting to infinite buffer, infinite population, and FIFO policy. This gives the common shorthand forms:

- **M/M/1** -- Markov arrivals, exponential service, 1 server
- **M/M/k** -- Markov arrivals, exponential service, k servers
- **M/M/k/k** -- k servers with k buffer slots (used in [[loss-systems]])

The three process types:
1. **Deterministic (D)** -- predictable, constant inter-arrival/service times
2. **Markov (M)** -- memoryless; arrivals follow Poisson distribution, inter-arrival and service times follow exponential distribution
3. **General (G)** -- completely arbitrary

## Prerequisites

- [[queueing-theory]] — Kendall notation is the standard classification system for queueing models
- [[arrival-rate-and-service-rate]] — The notation describes the distribution of arrival and service processes

## Lectures

- [[L32-Convergence-Ergodicity-Applications]]

## Related Concepts

- [[mm1-queue]]
- [[mmk-queue]]
- [[markov-process]]
- [[loss-systems]]
