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
  - "[[configuration-as-code]]"
---

# Terraform

Terraform is a tool for managing [[infrastructure-as-code]]. Its purpose is to manage the configuration of cloud infrastructure: you write configuration files that declare what services you want on your cloud provider (e.g., AWS), with what permissions and settings, and Terraform provisions them. It can also manage non-cloud resources like GitHub repository access and team membership.

Terraform supports a plan/apply workflow. The plan operation shows what will change before anything is actually modified, including expected cost differences. This lets you verify that a small change is indeed small and that you are not accidentally giving all your money to Amazon. If you are happy with the plan, you apply it. However, the plan is not perfect -- some things like unique identifiers are only known after creation, and state can change between plan and apply.

Destructive changes in Terraform are particularly dangerous. You could accidentally tell it to destroy all GitHub groups and it will gladly comply. Restoring information after a destructive change is not always as simple as reverting the configuration -- destroying a database and then re-creating it does not restore the contents. Non-destructive changes are easier to recover from since you can just make another PR to correct them.

## Prerequisites

- [[infrastructure-as-code]] — Terraform is a specific tool for implementing infrastructure as code
- [[configuration-as-code]] — Terraform applies the configuration-as-code principle to cloud infrastructure

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[infrastructure-as-code]]
- [[configuration-as-code]]
- [[rollback]]
- [[devops]]
