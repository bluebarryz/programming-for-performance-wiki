---
tags:
  - concept
  - ece459
  - testing
prerequisites:
  - "[[load-testing]]"
  - "[[observability]]"
  - "[[percentiles]]"
---

# Evaluating Load Test Success

Load test evaluation produces two kinds of answers: "Can the system handle a load of X?" (yes/no) and "What is the maximum load Y the system can handle?" If you know Y, answering whether it can handle X is straightforward. Finding Y may be harder because generating test data or load might increase faster than the rate of load added to the system, crossing into [[stress-testing]].

The maximum rate Y may represent a hard stop (crash, out of memory, rejected requests) or a degradation of service (performance dropping below a target or minimum). [[Observability]] helps gather the data needed for evaluation -- monitoring or logging that tracks when events start and end. Key questions include: Is total work completed within the total time limit? Did individual items complete within their per-item time limit 99% of the time or more?

Raw test results are often not sufficient to declare pass or fail. Post-processing to aggregate and analyze the data is needed, and manual correlation with other known factors may be necessary, especially when testing on separate hardware or instances. Looking at [[percentiles]] rather than just averages is important for meaningful evaluation.

## Prerequisites
- [[load-testing]] — Evaluation criteria define whether a load test passes or fails
- [[observability]] — Monitoring and logging provide the raw data for evaluation
- [[percentiles]] — Percentiles reveal whether time limits are met for most requests, not just on average

## Lectures

- [[L25-Load-Testing]]

## Related Concepts

- [[load-testing]]
- [[load-testing-planning]]
- [[percentiles]]
- [[aggregate-measures]]
- [[observability]]
- [[stress-testing]]
