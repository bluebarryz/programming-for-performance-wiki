---
tags:
  - concept
  - ece459
  - devops
  - security
lectures:
  - L35
prerequisites:
  - "[[devops]]"
  - "[[monitoring-and-alerting]]"
---

# Security in DevOps

Having an always-available service accessible over the internet makes security a major concern. While you can run security analysis on code offline, once the service is online the risk is enormous. The lecture highlights two categories of vulnerability as being especially bad: code execution/injection and data leakage ([[information-exposure]]).

Code execution means attackers run their own code on your platform. They can mess with your data, send spam, take services without paying, mine bitcoin at your expense, and more. Sometimes these are company-ending events. The [[cryptomining-abuse]] example illustrates how attackers exploit free CI/CD resources to mine cryptocurrency, bypassing CAPTCHAs and disguising their containers with innocuous names.

Beyond monitoring for performance and availability, security monitoring is essential. Cryptomining is relatively easy to spot because of its high CPU usage, but stealthy attacks that quietly exfiltrate data are much harder to detect and potentially more costly. The lecture also covers [[vulnerability-management]] and [[supply-chain-attacks]] as key security concerns in the DevOps context.

## Prerequisites

- [[devops]] — Security is an operational concern that DevOps teams must address
- [[monitoring-and-alerting]] — Security monitoring builds on the same monitoring infrastructure used for availability

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[cryptomining-abuse]]
- [[information-exposure]]
- [[vulnerability-management]]
- [[supply-chain-attacks]]
- [[monitoring-and-alerting]]
