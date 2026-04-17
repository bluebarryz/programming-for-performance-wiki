---
tags:
  - concept
  - ece459
  - devops
  - security
lectures:
  - L35
prerequisites:
  - "[[security-in-devops]]"
  - "[[monitoring-and-alerting]]"
---

# Information Exposure

Information exposure (data leakage) is one of the most dangerous security vulnerabilities for an always-available service. It is not only terrible for a company's reputation but also violates privacy laws and data protection regulations like the EU's GDPR. Fines can be enormous -- Amazon Europe holds the record at 746 million EUR (over a billion CAD). Other major offenders include Facebook (Meta), Google, and even H&M.

Most companies that get fined are penalized for insufficient technical measures -- they did not do enough to prevent data from reaching the wrong hands. A particularly dangerous pattern is when personally-identifiable information (PII) ends up in logs. As long as the logs are secure, it seems harmless, but if an attacker gains access to the logs, they get a one-stop-shop for everything they should not be able to see.

The reason PII often ends up in logs is that security policies forbid developers from accessing production databases, so excessive data gets logged for debugging purposes. This is an example of how overly restrictive security policies can backfire -- like password policies so strict that users write passwords on sticky notes.

## Prerequisites

- [[security-in-devops]] — Information exposure is one of the most dangerous security vulnerabilities
- [[monitoring-and-alerting]] — Detecting data leakage requires security monitoring

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[security-in-devops]]
- [[vulnerability-management]]
- [[cryptomining-abuse]]
