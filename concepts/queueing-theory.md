---
tags:
  - concept
  - ece459
  - queueing-theory
  - performance
lectures:
  - L31
  - L32
  - L33
prerequisites:
  - "[[scalability]]"
  - "[[bandwidth-vs-latency]]"
---

# Queueing Theory

Queueing theory is the mathematical study of queues: what makes them appear, how they behave, and how to make them go away. It provides a formal framework for reasoning about system performance rather than guessing.

Queueing theory is applicable to many fields: call centres, telecom systems, industrial design, and computers executing transactions. In the context of programming for performance, it helps answer questions like:

- Should we use one fast server or many slow ones?
- How does doubling the arrival rate affect response time?
- Is load balancing worth the effort?
- Can we give priority to certain jobs without harming others?
- How does job size variability affect scheduling policy choices?

The key insight is that these questions cannot be answered by intuition alone -- the answers are often counterintuitive (e.g., doubling both arrival and service rates actually halves mean response time, rather than keeping it the same).

## Prerequisites

- [[scalability]] — Queueing theory formalizes reasoning about system performance under load, which is what scalability measures
- [[bandwidth-vs-latency]] — Queueing models analyze throughput (bandwidth) and response time (latency) tradeoffs

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]
- [[L32-Convergence-Ergodicity-Applications]]
- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[queueing-terminology]]
- [[arrival-rate-and-service-rate]]
- [[littles-law]]
- [[mm1-queue]]
- [[mmk-queue]]
- [[kendall-notation]]
