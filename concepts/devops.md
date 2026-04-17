---
tags:
  - concept
  - ece459
  - devops
lectures:
  - L34
  - L35
prerequisites:
  - "[[scalability]]"
---

# DevOps

DevOps (also called Software Reliability Engineering) is the trend away from strict separation between a development team that writes software and an operations team that runs the software and infrastructure. At startups the separation is nonexistent -- there is no money for separate teams -- but even at larger companies, shifting all operational work to a dedicated operations team creates bottlenecks and misaligned incentives.

The core argument for DevOps is that if developers feel the pain of operations (being paged at night, dealing with deployment issues), they are motivated to build proper management tools, write better tests, and establish good deployment procedures. When operations is "someone else's problem," those improvement tickets never make it to the top of the backlog.

The DevOps topics covered in this course span two lectures: [[L34-DevOps-Configuration]] covers configuration (CI, configuration as code, infrastructure as code, containers, Kubernetes, naming, canary deployments) and [[L35-DevOps-Operations]] covers operations (monitoring, alerting, incident reports, security). The theme is using software development skills in operations contexts like system administration and database management.

## Prerequisites

- [[scalability]] — DevOps practices aim to maintain performance and scalability of deployed systems

## Lectures

- [[L34-DevOps-Configuration]]
- [[L35-DevOps-Operations]]

## Related Concepts

- [[continuous-integration]]
- [[configuration-as-code]]
- [[monitoring-and-alerting]]
- [[incident-reports]]
