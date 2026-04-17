---
tags:
  - concept
  - ece459
  - devops
  - deployment
lectures:
  - L34
prerequisites:
  - "[[continuous-integration]]"
  - "[[cattle-not-pets]]"
  - "[[rollback]]"
---

# Canary Deployment

A canary deployment is a strategy for testing a deployment by rolling it out incrementally rather than all at once. There are two main approaches. The first is to deploy the new software alongside the existing software and redirect a small fraction of traffic to the new service. If it works well, increase the fraction; if not, take it out of service. The second approach upgrades only some instances of the service (the "canaries") and checks whether they work as expected.

For the second kind, the basic steps are: stage for deployment, remove canary servers from service, upgrade them, run automatic tests on the upgraded canaries, reintroduce them into service, and observe how it goes. This is sometimes called "testing in prod" because real-life conditions are rarely replicated in test environments.

Canary deployments should be paired with the ability to [[rollback]]. If the canary deployment causes database schema changes shared across all servers, rollback becomes much harder -- you might need a reverse database migration, which may not always be possible if the migration is destructive.

## Prerequisites

- [[continuous-integration]] — Canary deployments are part of the CI/CD pipeline
- [[cattle-not-pets]] — Canary deployments require interchangeable server instances
- [[rollback]] — Canary deployments must be paired with the ability to rollback

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[rollback]]
- [[continuous-integration]]
- [[kubernetes]]
- [[cattle-not-pets]]
