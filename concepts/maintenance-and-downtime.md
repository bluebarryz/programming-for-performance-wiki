---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[multiple-services]]"
  - "[[service-interchangeability]]"
---

# Maintenance and Downtime

In real queueing systems, services will have downtime -- both planned and unplanned. This complicates simple queueing models because it means closing the queue and redirecting requesters elsewhere. If the pizza place's oven breaks, they cannot make any more pizza, and everyone in line must find somewhere else to eat.

We do not usually account for downtime directly when planning and designing our systems, partly because we expect things to always be available and rely on on-call staff to fix issues quickly. However, we might account for regular maintenance or planned downtime in our estimates of how many customers we can serve in a given period.

New services can also come online, which is the reverse of downtime. Like a new restaurant opening in a food hall, it changes the dynamics of the system. In reality, a new service is rarely a true surprise -- it takes time to build, test, and deploy. The [[fastpass-case-study]] discusses how the simulation may not fully account for ride downtime, which would cause additional downstream effects like compensatory FastPasses increasing the number of passes in circulation.

## Prerequisites

- [[multiple-services]] — Downtime of one service redirects customers to other services
- [[service-interchangeability]] — Whether customers can switch services during downtime depends on interchangeability

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[multiple-services]]
- [[service-interchangeability]]
- [[fastpass-case-study]]
