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
  - "[[vulnerability-management]]"
  - "[[profiling]]"
---

# Supply Chain Attacks

A supply chain attack compromises a dependency of the target software rather than the software itself. The term comes from physical manufacturing: building a gaming PC requires many components from many suppliers, and if any one of them is unavailable or compromised, the end product is affected. Similarly, modern software is built compositionally -- app A depends on libraries B, C, D, each of which has its own dependencies E, F, G, H, and compromising any one of them can result in a vulnerability in A.

The 2024 xz/liblzma vulnerability is a prominent example discussed in the course. A backdoor was discovered in the xz compression library, which some versions of openssh depend on. Since openssh is the secure shell daemon, being able to exploit it means root access and arbitrary code execution on vulnerable servers. The backdoor was discovered via performance profiling -- the injected code made the openssh server run noticeably slower (0.8s vs 0.3s for a connection attempt), which is directly relevant to a course on programming for performance.

The details of how the vulnerability was implemented and the social engineering needed to land it in the codebase are complex, but the key lesson for this course is that defending against known library vulnerabilities is not enough. An attacker can compromise a trusted dependency at the source, making the attack very difficult to detect through normal vulnerability scanning.

## Prerequisites

- [[security-in-devops]] — Supply chain attacks are a category of security vulnerability in deployed systems
- [[vulnerability-management]] — Standard vulnerability scanning may not catch supply chain attacks
- [[profiling]] — The xz backdoor was discovered through performance profiling (slower connection times)

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[vulnerability-management]]
- [[security-in-devops]]
- [[information-exposure]]
