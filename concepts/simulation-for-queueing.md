---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[mm1-queue]]"
  - "[[priority-queuing]]"
  - "[[multiple-services]]"
---

# Simulation for Queueing

At some point, a queueing theory problem becomes so complex that analytical reasoning with spreadsheets or hand calculations hits a limit. Simulation allows us to validate our theories by modeling the system computationally. The [[fastpass-case-study]] is a prime example: a theme park with many rides, different user types, priority systems, maintenance windows, and varying willingness to wait cannot be captured by a simple M/M/k model.

The simulation for the Disney case models several realistic aspects: every customer is an independent agent with different arrival/departure times, preferences, and willingness to wait; the park has opening and closing times; each service has its own service rate and can go down for maintenance; and services have fixed maximum capacity. User archetypes represent different "personalities" -- annual pass holders who can return another day, versus one-time visitors who do not want to miss out.

Simulation is complementary to analytical queueing theory. While analytical models give exact solutions for simplified systems (M/M/1, M/M/k), simulation handles the messy reality of multiple interacting queues, heterogeneous users, and complex priority rules. The simulation code for the FastPass study is available as open-source Python code.

## Prerequisites

- [[mm1-queue]] — Simulation handles cases too complex for analytical M/M/1 or M/M/k models
- [[priority-queuing]] — Complex priority systems are a key motivation for using simulation
- [[multiple-services]] — Heterogeneous services with interacting queues require simulation to analyze

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[fastpass-case-study]]
- [[priority-queuing]]
- [[virtual-queues]]
- [[balking]]
