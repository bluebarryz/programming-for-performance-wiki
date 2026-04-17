---
tags:
  - lecture
  - ece459
  - devops
  - operations
  - security
lecture: 35
title: "DevOps: Operations"
prerequisite_lectures:
  - "[[L34-DevOps-Configuration]]"
  - "[[L24-Profiling-Observing-Operations]]"
---

# L35 - DevOps: Operations

This lecture covers the operational side of DevOps: keeping services running and secure. It starts with monitoring (health checks, CPU load, memory, disk, network, queue lengths, response times) and alerting (alerts vs. tickets vs. logging). It stresses the importance of judicious alerting to avoid alert fatigue. The lecture covers incident reports/post-mortems, including the distinction between root causes and proximate causes, Toyota's Five Whys technique, and what should (and should not) appear in a report. The security section covers code execution/injection vulnerabilities, information exposure (GDPR fines), the xz/openssh supply chain attack (discovered via performance profiling), defending against known vulnerabilities in dependencies, and the abuse of free cloud services for cryptocurrency mining.

## Prerequisite Lectures
- [[L34-DevOps-Configuration]] — Need DevOps fundamentals and infrastructure setup before operations
- [[L24-Profiling-Observing-Operations]] — Need observability concepts for monitoring and alerting

## Concepts Covered

- [[monitoring-and-alerting]]
- [[health-checks]]
- [[alert-fatigue]]
- [[incident-reports]]
- [[root-cause-vs-proximate-cause]]
- [[five-whys]]
- [[security-in-devops]]
- [[supply-chain-attacks]]
- [[vulnerability-management]]
- [[information-exposure]]
- [[cryptomining-abuse]]
