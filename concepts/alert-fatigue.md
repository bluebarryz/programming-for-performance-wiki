---
tags:
  - concept
  - ece459
  - devops
  - operations
lectures:
  - L35
prerequisites:
  - "[[monitoring-and-alerting]]"
---

# Alert Fatigue

Alert fatigue occurs when alerts are too common, causing people to ignore them. The lecture draws an analogy to fire alarms: when you hear one, your first thought is probably not "the building is on fire" but rather "some jerk pulled the alarm." Because we have experienced too many false alarms, we assume any alarm is a false one. But if there is an actual fire, that assumption could be deadly.

It is very important to be judicious about the use of alerts. If alerts are too frequent or too noisy, the on-call person will stop taking them seriously, defeating the entire purpose of the alerting system. The response categories -- alerts (act now), tickets (act soon), and logging (forensic only) -- help reduce fatigue by ensuring only truly urgent issues trigger an immediate alert.

Developers who are woken up in the middle of the night by a spurious alert are strongly motivated to improve monitoring, testing, and deployment processes to prevent it from happening again. This pain-driven improvement is actually a feature of DevOps culture.

## Prerequisites

- [[monitoring-and-alerting]] — Alert fatigue is a failure mode of poorly configured alerting systems

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[monitoring-and-alerting]]
- [[health-checks]]
- [[devops]]
