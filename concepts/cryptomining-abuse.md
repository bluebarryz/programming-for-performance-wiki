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
  - "[[continuous-integration]]"
---

# Cryptomining Abuse

Cryptomining abuse refers to attackers exploiting free compute resources (such as cloud provider free tiers or CI/CD platforms like GitHub Actions) to mine cryptocurrency. Security researchers have documented massive operations that abuse build and deployment systems for this purpose.

The attack involves bypassing normal signup limitations -- defeating CAPTCHAs and scripting browser interactions to look like a human -- to create large numbers of accounts. The return on investment is poor from the attacker's perspective (roughly $137 worth of cryptocurrency from $103,000 of resources, a 0.13% return), but since the attacker pays nothing and the platform foots the bill, it is essentially free money. The mining images and apps are given inconspicuous names (e.g., "linux88884474") and random GitHub action names to avoid detection.

Cryptomining is somewhat easier to spot than other malicious activity because it is CPU-intensive. Unusual CPU consumption by an unexplained container is a red flag. More dangerous are stealthy attacks like data exfiltration, which quietly observe and send information without obvious resource consumption.

## Prerequisites

- [[security-in-devops]] — Cryptomining abuse is a code execution attack exploiting cloud resources
- [[monitoring-and-alerting]] — Cryptomining is detectable through CPU usage monitoring
- [[continuous-integration]] — Attackers exploit free CI/CD resources like GitHub Actions for mining

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[security-in-devops]]
- [[monitoring-and-alerting]]
- [[information-exposure]]
- [[supply-chain-attacks]]
