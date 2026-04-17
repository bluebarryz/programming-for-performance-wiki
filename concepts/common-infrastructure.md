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

# Common Infrastructure

Common infrastructure refers to the practice of viewing different parts of your infrastructure as services with interfaces, where communication happens exclusively via the interface or API. This reduces coupling between components and allows you to scale the parts that need scaling independently.

Rather than building everything yourself, it is usually better to use existing tools -- whether open-source, commercial, or provided by your cloud platform. Examples include storage layers (MongoDB, S3), naming and discovery services (Consul), and monitoring tools (Prometheus). Rolling your own should be a last resort, especially for anything security or encryption related, where the risk of creating a vulnerable system far outweighs the benefits.

However, patience is sometimes the best strategy. Cloud platforms like AWS constantly launch new managed services, and investing heavily in building a feature only to have your provider offer it as a managed service shortly after can be frustrating. If what you are looking for does not exist yet, consider whether there is a good reason for that.

## Prerequisites

- [[infrastructure-as-code]] — Common infrastructure builds on managing infrastructure programmatically
- [[devops]] — Using shared services and APIs is a DevOps best practice

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[infrastructure-as-code]]
- [[configuration-as-code]]
- [[service-naming]]
- [[devops]]
