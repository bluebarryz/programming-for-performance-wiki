---
tags:
  - concept
  - ece459
  - testing
prerequisites:
  - "[[load-testing]]"
  - "[[observability]]"
---

# Load Testing Planning

A load testing plan needs to answer who, what, where, when, and why. The "why" determines the kind of test. The plan must define at minimum: what will be tested (which workflows), how it will be tested (the test scenario), and how success or failure will be determined.

A simple scenario example: "we will test saving things to the database by generating 10,000 update-account requests, submit them all at once, and the total time to complete all transactions should not exceed 15 seconds." This covers what to test, how to test it, and how to evaluate success. The level of detail and number of sign-offs depends on the organization -- some companies require justification for the time invested since load testing has high cost and effort.

Choosing which workflows to test is critical. Aiming for 100% coverage is unnecessary and expensive. Focus on workflows that are already known to be slow (rate-limiting), on the critical path, or identified by [[observability]] as bottlenecks. For new systems, identify computationally intensive or user-experience-critical workflows. External requirements (like transaction response time limits) also drive testing priorities.

## Prerequisites
- [[load-testing]] — Planning requires understanding what load testing aims to achieve
- [[observability]] — Bottleneck identification from observability drives which workflows to test

## Lectures

- [[L25-Load-Testing]]

## Related Concepts

- [[load-testing]]
- [[load-testing-principles]]
- [[evaluating-load-test-success]]
- [[observability]]
