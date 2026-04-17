---
tags:
  - concept
  - ece459
  - devops
  - deployment
lectures:
  - L34
prerequisites:
  - "[[canary-deployment]]"
  - "[[terraform]]"
  - "[[configuration-as-code]]"
---

# Rollback

Rollback is the ability to revert a deployment to a previous version when something goes wrong. Systems should be designed so that rollback is always possible. This is especially important when using [[canary-deployment]] strategies, where the whole point is to detect problems early and revert if needed.

Rollback becomes significantly harder when a deployment involves shared state changes, particularly database schema migrations. If the canary deployment changes the database table structure and this database is shared across all servers, deploying the change can break the old servers, and rolling back requires writing a reverse migration -- which may not be possible if the migration was destructive (e.g., dropping a column or table).

With [[terraform]], destructive changes are particularly dangerous. You could accidentally tell it to destroy all GitHub groups and it will carry out the instruction. Restoring information after a destructive change might not be as simple as reverting -- if you destroy a database, reverting the configuration recreates the database but not its contents. This is why backups and careful review of change plans are essential.

## Prerequisites

- [[canary-deployment]] — Rollback is essential when canary deployments detect problems
- [[terraform]] — Destructive Terraform changes make rollback especially important and sometimes impossible
- [[configuration-as-code]] — Rollback relies on version-controlled configuration to revert changes

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[canary-deployment]]
- [[kubernetes]]
- [[terraform]]
- [[continuous-integration]]
