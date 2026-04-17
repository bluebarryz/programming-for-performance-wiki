---
tags:
  - concept
  - ece459
  - devops
  - operations
lectures:
  - L35
prerequisites:
  - "[[devops]]"
  - "[[observability]]"
  - "[[health-checks]]"
---

# Monitoring and Alerting

Monitoring is the practice of observing system behavior to detect problems. It is surprisingly difficult to do well. Applications should have [[health-checks]], but monitoring goes beyond simple up/down status to include CPU load, memory utilization, disk space, disk I/O, network traffic, clock skew, queue lengths, and application response times.

Interpreting monitoring data requires context. High CPU usage at 80% might be fine if the system is keeping up with its workload, but 100% means performance is CPU-bound. Long queue lengths might be acceptable unless they cause missed deadlines. The lesson from Sherlock Holmes applies: the dog that did not bark can also be a clue -- if nobody has logged in for an unusually long time, something might be wrong.

Alerting builds on monitoring by automatically notifying people when conditions or thresholds are breached. Niall Murphy categorizes responses into three tiers: alerts (a human must act now), tickets (a human must act soon, within hours or days), and logging (no action needed except for forensic/diagnostic purposes). A common anti-pattern is "logs-as-tickets" where people routinely scan logs to find errors -- instead, write code to scan logs automatically. Being judicious about alerts is critical to avoiding [[alert-fatigue]].

## Prerequisites

- [[devops]] — Monitoring and alerting is the operational side of DevOps
- [[observability]] — Monitoring builds on the observability practices of measuring and understanding system behavior
- [[health-checks]] — Health checks are the foundation that monitoring systems build upon

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[alert-fatigue]]
- [[health-checks]]
- [[incident-reports]]
- [[devops]]
