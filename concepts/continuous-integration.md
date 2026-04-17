---
tags:
  - concept
  - ece459
  - devops
  - deployment
lectures:
  - L34
prerequisites:
  - "[[devops]]"
---

# Continuous Integration

Continuous integration (CI) is the practice of automatically building and testing each change (or related group of changes) as it is made. The process is straightforward: pull code from version control, build, run tests, and report results. These steps are triggered automatically on every commit, with results sent via email, Slack, or similar channels.

This is now considered a best practice. In the past, integrating code changes did not happen on every build -- it might be done nightly or less frequently. That approach was slow and expensive. With modern version control, good tests, and scripted deployments, there is no reason not to integrate continuously.

A key social convention that accompanies CI is not breaking the build. When someone does break it, the CI system immediately notifies the team, making it clear who needs to fix the problem. This fast feedback loop is central to the DevOps philosophy.

## Prerequisites

- [[devops]] — CI is a core DevOps practice for automating builds and tests

## Lectures

- [[L34-DevOps-Configuration]]

## Related Concepts

- [[configuration-as-code]]
- [[canary-deployment]]
- [[devops]]
