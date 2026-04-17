---
tags:
  - concept
  - ece459
  - testing
prerequisites:
  - "[[load-testing]]"
---

# Constant Vigilance

Load testing captures the state of things at a single point in time and must be repeated regularly to catch performance degradations. Software grows in complexity and functionality over time, both of which tend to make it slower. Improved hardware offsets some of this, but in the current era of incremental improvements rather than big leaps, it is not enough to rely on hardware alone.

Performance regressions are rarely intentional -- they accumulate gradually as features are added and code grows. Repeating load tests regularly catches major regressions before they become customer-facing problems. The course cites arewefastyet.com as a real-life example: it tracks regressions and improvements in Firefox performance continuously.

If a load test fails, the course recommends identifying specific scenarios to improve, applying optimization techniques, re-running the test, and re-evaluating. This cycle repeats until the scenario passes. If the limits of software optimization are reached, a major redesign may be needed -- or the problem can be reframed (e.g., spreading billing across a month instead of doing it all on one day).

## Prerequisites
- [[load-testing]] — Constant vigilance means repeating load tests regularly as software evolves

## Lectures

- [[L25-Load-Testing]]

## Related Concepts

- [[load-testing]]
- [[endurance-testing]]
- [[observability]]
- [[premature-optimization]]
