---
tags:
  - lecture
  - ece459
  - queueing-theory
  - performance
  - simulation
lecture: 33
title: More Advanced Queueing Theory
prerequisite_lectures:
  - "[[L31-Introduction-to-Queueing-Theory]]"
  - "[[L32-Convergence-Ergodicity-Applications]]"
---

# L33 - More Advanced Queueing Theory

This lecture extends basic queueing theory with real-world complications. It discusses multiple heterogeneous services (where not every server can handle every request type), service interchangeability (total, partial, or none), and planned/unplanned maintenance. It covers queue behaviours when queues are too long: balking (not joining), reneging (leaving mid-wait), and loss (capacity refusal, M/M/k/k systems). Priority queuing is explored in depth through the Disney FastPass case study, which uses simulation to compare no-priority, FastPass (virtual queue), and FastPass++ (advance reservation) systems. Key findings: priority systems reduce overall wait times by redistributing demand to under-utilized services, but can increase inequality among users. The lecture concludes with lessons about how complex priority systems can be exploited by expert users and the importance of simulation for validating complex queueing models.

## Prerequisite Lectures
- [[L31-Introduction-to-Queueing-Theory]] — Need queueing fundamentals (arrival/service rates, utilization, open/closed systems)
- [[L32-Convergence-Ergodicity-Applications]] — Need M/M/1, M/M/k models and Little's Law before advanced extensions

## Concepts Covered

- [[multiple-services]]
- [[service-interchangeability]]
- [[maintenance-and-downtime]]
- [[balking]]
- [[reneging]]
- [[loss-systems]]
- [[priority-queuing]]
- [[virtual-queues]]
- [[simulation-for-queueing]]
- [[fastpass-case-study]]
