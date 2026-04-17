---
tags:
  - concept
  - ece459
  - devops
  - infrastructure
lectures:
  - L34
prerequisites:
  - "[[infrastructure-as-code]]"
  - "[[devops]]"
---

# Cattle, Not Pets

The "cattle, not pets" philosophy says that servers (including virtual machines and containers) should be treated as interchangeable members of a herd rather than as individually-maintained pets. Pets are unique, given individual attention, and treated differently from one another. Cattle are dealt with as a group -- you move the whole herd along and do what they need uniformly.

This philosophy means having a reproducible process for deployment with minimal manual intervention, ideally zero. The benefits are significant: saving hours of setup time, reducing human errors, and enabling automatic scaling (starting and stopping servers based on demand).

In a world with [[containers]] and virtualization, there is no reason to worry about individual differences between servers. Tools like [[kubernetes]] embody this philosophy by automating deployment, scaling, load balancing, and health monitoring of container instances, replacing them automatically if they die.

## Prerequisites

- [[infrastructure-as-code]] — Treating servers as cattle requires reproducible, automated provisioning
- [[devops]] — The cattle-not-pets philosophy is a core DevOps principle for deployment

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[containers]]
- [[kubernetes]]
- [[infrastructure-as-code]]
- [[service-interchangeability]]
