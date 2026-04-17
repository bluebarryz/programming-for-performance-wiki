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
  - "[[devops]]"
---

# Incident Reports

An incident report (or post-mortem) is a structured document produced after an incident to identify root causes and capture lessons learned. If you do not find the root cause, the same problem can recur. If you do not learn anything, it is bad for both the company and your own career growth. A report is worth doing even if it is not fun.

A good incident report contains: a clear timeline of events (when the problem started, when it was noticed, what actions were taken, when it was resolved), analysis of root causes and [[root-cause-vs-proximate-cause|proximate causes]], action items for short-term fixes and long-term prevention, and lessons learned. Action items must be realistic -- suggesting a full rewrite in Rust is factually nice but unlikely to happen.

Equally important is what should not be in an incident report: irrelevant detail that distracts from the point, speculation (educated guessing is fine but baseless speculation is not), and blaming or shaming. Blaming is counterproductive because it incentivizes covering up incidents, shifting blame to others, and creates a culture of fear rather than learning. The medical field has extensive research showing that blame-oriented cultures produce worse patient outcomes compared to learning cultures.

## Prerequisites

- [[monitoring-and-alerting]] — Incidents are detected through the monitoring and alerting system
- [[devops]] — Post-mortems are a core DevOps practice for learning from failures

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[root-cause-vs-proximate-cause]]
- [[five-whys]]
- [[monitoring-and-alerting]]
- [[devops]]
