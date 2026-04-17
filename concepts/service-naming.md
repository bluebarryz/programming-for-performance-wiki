---
tags:
  - concept
  - ece459
  - devops
  - infrastructure
lectures:
  - L34
prerequisites:
  - "[[common-infrastructure]]"
  - "[[devops]]"
---

# Service Naming

Naming is one of the classic hard problems in computing (alongside cache invalidation and off-by-one errors). In the DevOps context, debates rage about whether teams, services, and resources should have "meaningful" descriptive names or arbitrary ones.

Descriptive names like "billing" help indicate what a service does, but create confusion: does "billing" refer to the service or the team? What happens when you replace the billing service -- is the new one "billing2"? What if billing and accounting merge? On the other hand, allegedly-descriptive names like "X infrastructure" and "X operations" can result in 35% of queries going to the wrong team.

The real solution is service discovery: a directory tool where you can look up "potato" (or any service name) and be sent to the right place. Tools like OpsLevel provide this, along with information about service maturity -- whether deprecated things are in use, whether security vulnerabilities are unpatched, whether test coverage is sufficient. There are also morale implications: teams named after mythological or fictional references (like "Avengers, Assemble") can foster team identity and belonging.

## Prerequisites

- [[common-infrastructure]] — Service naming and discovery are part of managing shared infrastructure
- [[devops]] — Naming conventions arise from the need to organize services in a DevOps environment

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[common-infrastructure]]
- [[devops]]
- [[multiple-services]]
