---
tags:
  - concept
  - ece459
  - queueing-theory
  - case-study
lectures:
  - L33
prerequisites:
  - "[[priority-queuing]]"
  - "[[virtual-queues]]"
  - "[[simulation-for-queueing]]"
  - "[[balking]]"
  - "[[reneging]]"
---

# FastPass Case Study

The FastPass case study uses the history of Disney's FastPass system (analyzed via the Defunctland channel) as a real-world application of queueing theory and simulation. The theme park setting is complex enough that analytical queueing models become insufficient and simulation is required to evaluate different priority systems.

The simulation compares three systems: no priority (everyone is equal), FastPass (virtual queue with a return time ticket for popular rides), and FastPass++ (advance reservation of priority passes for specific attractions). Key results include: without priority, the average number of rides is 3.31; with FastPass it rises to 3.77; and with FastPass++ it reaches 4.23. FastPass reduces actual wait times to about 2/3 of the no-priority baseline by encouraging people to visit less popular attractions while waiting for their return time.

The important lessons are that priority systems do not significantly increase wait times for the most popular attractions, but they do encourage better utilization of less popular ones and increase overall usage. However, FastPass++ increases inequality -- some knowledgeable guests get 8-9 rides while unaware guests get only 1-2. The more complex a system, the more it can be exploited by those who understand its nuances, which can mess up capacity planning.

## Prerequisites

- [[priority-queuing]] — FastPass is fundamentally a priority queuing system
- [[virtual-queues]] — FastPass implements virtual queues where guests get return-time tickets
- [[simulation-for-queueing]] — The case study uses simulation because the system is too complex for analytical models
- [[balking]] — Guest behavior includes balking when queues are too long
- [[reneging]] — Guest behavior includes reneging when waits exceed expectations

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[priority-queuing]]
- [[virtual-queues]]
- [[simulation-for-queueing]]
- [[balking]]
- [[reneging]]
