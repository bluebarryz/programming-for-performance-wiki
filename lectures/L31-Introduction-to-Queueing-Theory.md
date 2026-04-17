---
tags:
  - lecture
  - ece459
  - queueing-theory
  - performance
lecture: 31
title: Introduction to Queueing Theory
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
---

# L31 - Introduction to Queueing Theory

This lecture introduces queueing theory as a formal framework for reasoning about system performance instead of guessing. It defines core terminology (server, customer, wait time, service time, arrival rate, service rate, utilization, queue length, response time, residence time, throughput) and their mathematical symbols. Through examples, it shows that doubling both arrival and service rates more than halves response time, that bottleneck devices limit improvements in closed systems, and that the choice between one fast server vs. many slow ones depends on job size variability and preemptibility. The lecture covers load balancing policies (random, round-robin, shortest-queue, size-interval-task-assignment, least-work-left, central-queue), the "red line overload" condition where arrival rate exceeds service rate, and the difference between open and closed systems for measuring service rate.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Need scalability, bandwidth, and latency fundamentals

## Concepts Covered

- [[queueing-theory]]
- [[queueing-terminology]]
- [[arrival-rate-and-service-rate]]
- [[utilization]]
- [[open-vs-closed-systems]]
- [[bottleneck-device]]
- [[load-balancing]]
- [[task-assignment-policies]]
- [[red-line-overload]]
- [[one-fast-server-vs-many-slow]]
- [[measuring-service-rate]]
