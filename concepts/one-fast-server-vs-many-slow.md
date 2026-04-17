---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L31
prerequisites:
  - "[[queueing-theory]]"
  - "[[load-balancing]]"
---

# One Fast Server vs. Many Slow Servers

A common design question: is it better to have one server with speed s, or n servers each with speed s/n? The answer depends on several factors:

- **High job size variability**: multiple servers are better. A single large job can block one queue while other queues continue to serve small jobs.
- **Low load**: a single fast server is preferable because multiple slow servers would mostly sit idle.
- **Preemptible jobs**: a single fast server is at least as good, because it can simulate n slow servers through time-sharing.
- **Non-preemptible jobs**: it depends on the variability of job sizes.

This is one of the motivating questions of queueing theory -- the answer is "it depends" and requires formal analysis rather than intuition.

## Prerequisites

- [[queueing-theory]] — This is one of the motivating design questions that queueing theory addresses
- [[load-balancing]] — Multiple slow servers require a load balancing strategy

## Lectures

- [[L31-Introduction-to-Queueing-Theory]]

## Related Concepts

- [[queueing-theory]]
- [[load-balancing]]
- [[mm1-queue]]
- [[mmk-queue]]
