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
  - "[[cattle-not-pets]]"
---

# Containers

Containers are a lightweight alternative to full virtual machines for isolating applications. The evolution went from installing binaries and config files by hand, to packages with dependency lists, to virtual machines with full guest operating systems, and finally to containers. Each step solved problems introduced by the previous approach.

Virtual machines provide isolation but at the cost of each application having its own full guest OS, which is wasteful -- you end up installing the same security patch ten times. Containers give many of the same isolation advantages without nearly as much overhead. They are run by a container engine on top of the host OS, assembled from a specification of required libraries and tools, and share the host kernel (in read-only mode) where possible. A container is essentially a very lightweight VM.

The goal of the build process should be to produce a container ready to be deployed and managed by orchestration tools like [[kubernetes]]. One downside of containers is that they can let you keep old, insecure versions of libraries around indefinitely, since updates to shared libraries on the host no longer propagate into the container. Keeping on top of security updates remains important.

## Prerequisites

- [[infrastructure-as-code]] — Containers are built from configuration specifications, embodying IaC
- [[cattle-not-pets]] — Containers enable treating servers as disposable, interchangeable units

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[kubernetes]]
- [[cattle-not-pets]]
- [[infrastructure-as-code]]
- [[vulnerability-management]]
