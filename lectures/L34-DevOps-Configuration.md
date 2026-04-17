---
tags:
  - lecture
  - ece459
  - devops
  - infrastructure
  - deployment
lecture: 34
title: "DevOps: Configuration"
prerequisite_lectures:
  - "[[L30-Clusters-Cloud-Computing]]"
---

# L34 - DevOps: Configuration

This lecture introduces DevOps (also called Software Reliability Engineering) as the merging of development and operations responsibilities. It covers continuous integration as a best practice, then dives into the principle of treating configuration as code: using version control, code reviews, testing, and continuous builds for infrastructure configuration. Terraform is highlighted as a tool for infrastructure as code. The lecture discusses common infrastructure patterns (using APIs/interfaces, avoiding not-invented-here syndrome), naming conventions for services and teams, and the "servers as cattle, not pets" philosophy for reproducible deployments. It covers Kubernetes for container orchestration, canary deployments for safe rollouts, and the evolution from manual installation to packages to VMs to containers.

## Prerequisite Lectures
- [[L30-Clusters-Cloud-Computing]] — Need cloud computing and deployment concepts before DevOps configuration

## Concepts Covered

- [[devops]]
- [[continuous-integration]]
- [[configuration-as-code]]
- [[terraform]]
- [[infrastructure-as-code]]
- [[common-infrastructure]]
- [[service-naming]]
- [[cattle-not-pets]]
- [[kubernetes]]
- [[canary-deployment]]
- [[containers]]
- [[rollback]]
