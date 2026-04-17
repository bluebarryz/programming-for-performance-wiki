---
tags:
  - concept
  - ece459
  - devops
  - configuration
lectures:
  - L34
prerequisites:
  - "[[devops]]"
  - "[[continuous-integration]]"
---

# Configuration as Code

Configuration as code is the principle that system configuration should be treated like source code: version-controlled, reviewed, tested, and automatically applied. Complicated manual configuration leads to mistakes, and people will forget steps when following a wiki page or README. The solution is to make it automatic.

The key practices include: using version control on your configuration, implementing code reviews on configuration changes, testing that configurations generate expected files or spawn expected services, aiming for modular services that integrate smoothly, refactoring configuration files (such as Puppet manifests or Chef recipes), and using continuous builds. Configurations should "converge" -- unlike application code which terminates, configurations define indefinitely-running services, but resource usage (like CPU) should settle down.

[[Terraform]] is a specific tool that applies these principles to infrastructure. It lets you define your cloud infrastructure (services, permissions, etc.) in configuration files, supports a "plan" operation to preview changes before applying them, and can manage not just cloud resources but also things like GitHub repository access and team membership.

## Prerequisites

- [[devops]] — Configuration as code is a key DevOps principle
- [[continuous-integration]] — CI pipelines apply and test configuration changes automatically

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[infrastructure-as-code]]
- [[terraform]]
- [[continuous-integration]]
- [[devops]]
