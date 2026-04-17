---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
prerequisites:
  - "[[arrival-rate-and-service-rate]]"
  - "[[open-vs-closed-systems]]"
---

# Measuring Service Rate

The mean job size E[S] = 1/mu can be measured, but simply running isolated jobs does not reflect reality (caching effects, concurrent job interactions are missing). Two strategies exist depending on system type:

**Open system strategy**: ramp up the arrival rate lambda. Keep piling jobs on until the completion rate levels off. At that point, the system has hit its limit and we have mu.

**Closed system strategy**: ensure there is always work to do by setting think time to zero. Then measure the jobs completing per second directly, giving mu.

The IBM anecdote in the lecture emphasizes that you should never guess at mu -- always measure it under realistic conditions.

## Prerequisites

- [[arrival-rate-and-service-rate]] — Measuring mu requires understanding what service rate means
- [[open-vs-closed-systems]] — The measurement strategy differs between open and closed systems

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]

## Related Concepts

- [[arrival-rate-and-service-rate]]
- [[open-vs-closed-systems]]
- [[queueing-theory]]
