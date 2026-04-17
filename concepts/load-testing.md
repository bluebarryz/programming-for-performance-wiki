---
tags:
  - concept
  - ece459
  - testing
prerequisites:
  - "[[profiling]]"
  - "[[observability]]"
---

# Load Testing

Load testing relates performance to scalability -- taking software from 1 user to 100 to 10 million. It involves applying a specific target workload to a system and demonstrating that it can handle that amount. This is distinct from [[stress-testing]], which increases pressure until things break.

Common reasons for load testing include: understanding limits of a new system, verifying the system can handle expected workload increases, preparing for sudden spikes (like tax season), meeting high uptime requirements, or satisfying a project plan checkbox. Each reason implies a different kind of test. For new systems, understand the average workload. For expected increases, identify bottlenecks. For spikes, generate burst behavior. For uptime requirements, combine load with extended duration ([[endurance-testing]]).

Load testing requires profiling to find what is slow, and the results drive decisions about what to optimize. It is also useful for making estimates of maximum users or transactions a system can handle, which is a common question from management.

## Prerequisites
- [[profiling]] — Load testing requires profiling to identify what is slow
- [[observability]] — Observability tools gather the data needed to evaluate load test results

## Lectures

- [[L25-Load-Testing]]

## Related Concepts

- [[load-testing-planning]]
- [[load-testing-principles]]
- [[evaluating-load-test-success]]
- [[stress-testing]]
- [[endurance-testing]]
- [[constant-vigilance]]
