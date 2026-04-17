---
tags:
  - lecture
  - ece459
  - testing
  - scalability
  - performance
lecture: L25
title: Load Testing
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
  - "[[L24-Profiling-Observing-Operations]]"
---

# L25 - Load Testing

This lecture covers load testing as a means of relating performance to scalability. It distinguishes load testing (can the system handle a specific target load?) from stress testing (at what point does the system break?). Planning a load test requires answering who, what, where, when, and why. Key principles for meaningful tests include: the hardware principle (test on production-like hardware), the reality principle (use realistic workloads and data), the volume principle (use actual high volume, not simulated pressure), and reproducibility. The lecture also covers endurance testing (sustained load over time to catch memory leaks, resource exhaustion), how to evaluate success (maximum load Y, degradation of service), and the need for constant vigilance through repeated testing as software evolves.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Need scalability fundamentals before load testing
- [[L24-Profiling-Observing-Operations]] — Need profiling and observability basics before measuring system load

## Concepts Covered

- [[load-testing]]
- [[stress-testing]]
- [[load-testing-planning]]
- [[load-testing-principles]]
- [[endurance-testing]]
- [[evaluating-load-test-success]]
- [[constant-vigilance]]
