---
tags:
  - concept
  - ece459
  - devops
  - infrastructure
lectures:
  - L34
prerequisites:
  - "[[configuration-as-code]]"
  - "[[cloud-computing]]"
---

# Infrastructure as Code

Infrastructure as code (IaC) is the practice of managing and provisioning computing infrastructure through machine-readable configuration files rather than manual processes or interactive tools. It is closely related to [[configuration-as-code]] but specifically focuses on the infrastructure layer -- the servers, networks, and cloud resources that your code runs on.

The environment that your code runs in is itself a kind of configuration. Having a wiki page or GitHub document titled "How to Install AwesomeApp" is not sufficient because complicated manual steps lead to mistakes and forgotten steps. The solution is to make infrastructure provisioning automatic, version-controlled, and repeatable.

[[Terraform]] is a prominent example of infrastructure as code. You write configuration files declaring what services you want, with what permissions and settings, and Terraform provisions them on your cloud provider (e.g., AWS). It can also manage non-infrastructure resources like GitHub repository access and team membership. The plan/apply workflow lets you preview changes before committing to them.

## Prerequisites

- [[configuration-as-code]] — IaC applies the configuration-as-code principle specifically to infrastructure provisioning
- [[cloud-computing]] — IaC manages cloud resources like servers, networks, and storage programmatically

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[configuration-as-code]]
- [[terraform]]
- [[containers]]
- [[cattle-not-pets]]
- [[devops]]
