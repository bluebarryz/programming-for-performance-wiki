---
tags:
  - concept
  - ece459
  - testing
prerequisites:
  - "[[load-testing]]"
  - "[[load-testing-planning]]"
---

# Load Testing Principles

The course outlines several principles for meaningful load testing results. The **Hardware Principle** states that scalability testing must be done on the actual production hardware (or equivalent), since local development machines have very different limiting factors like RAM. The **Reality Principle** requires using realistic workloads -- actual customer data or the best approximation, since synthetic test data may not be representative (e.g., a test database much smaller than production can hide migration timeout issues).

The **Volume Principle** says "more is the new more" -- to see how a system performs under pressure, you must actually put it under pressure with real volume, not simulate it by limiting RAM or burning CPU cycles. Simulated pressure does not reproduce real-world effects like lock contention with 500 concurrent users. The **Reproducibility Principle** requires that two runs of the load test produce very similar results, though load testing inherently has more variance than unit testing due to randomness in workload generation and system scheduling.

User behavior is also hard to simulate accurately. Test scripts may not represent how real users behave -- a scenario assuming monthly report runs might miss that a manager actually runs the report hourly.

## Prerequisites
- [[load-testing]] — These principles govern how to conduct meaningful load tests
- [[load-testing-planning]] — Principles constrain and guide the test plan

## Lectures

- [[L25-Load-Testing]]

## Related Concepts

- [[load-testing]]
- [[load-testing-planning]]
- [[evaluating-load-test-success]]
- [[endurance-testing]]
