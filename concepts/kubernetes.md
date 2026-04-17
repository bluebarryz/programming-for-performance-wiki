---
tags:
  - concept
  - ece459
  - devops
  - infrastructure
lectures:
  - L34
prerequisites:
  - "[[containers]]"
  - "[[cattle-not-pets]]"
  - "[[load-balancing]]"
---

# Kubernetes

Kubernetes is an orchestration platform for automating the deployment and scaling of containerized applications. Rather than manually managing [[containers]], you tell Kubernetes what you want deployed and it handles the rest. It provides a framework for your environment that includes load balancing, automatic rollouts and reverts (if something goes wrong), determining what instances run on what hardware, checking the health of instances, replacing failed instances, and more.

Kubernetes embodies the [[cattle-not-pets]] philosophy. If you want to deploy a new version of a container, you do not manually update each instance -- you tell Kubernetes the desired state and it makes it happen. This enables automatic scaling (starting and stopping containers based on demand) and reduces the amount of manual intervention to ideally zero.

The goal of the build process should be to produce a container that is ready to be deployed and managed by Kubernetes. Combined with [[continuous-integration]] and [[canary-deployment]] strategies, Kubernetes enables a robust deployment pipeline where new versions can be rolled out gradually and rolled back automatically if problems are detected.

## Prerequisites

- [[containers]] — Kubernetes orchestrates containerized applications
- [[cattle-not-pets]] — Kubernetes embodies the cattle-not-pets philosophy with automated instance management
- [[load-balancing]] — Kubernetes handles load balancing across container instances

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[containers]]
- [[cattle-not-pets]]
- [[canary-deployment]]
- [[rollback]]
