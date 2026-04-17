---
tags:
  - lecture
  - ece459
  - cache
  - coherency
  - hardware
lecture: 8
title: Cache Coherency
date: 2024-09-10
prerequisite_lectures:
  - "[[L07-CPU-Hardware-Branch-Prediction]]"
---

# L08 - Cache Coherency

This lecture addresses the problem of keeping data consistent across multiple CPU caches. It walks through cache coherence protocols of increasing sophistication: write-through caches, write-back caches with the MSI protocol, and the widely-used MESI and MESIF protocols. It also covers false sharing as a practical performance pitfall, and a software implementation of MESI-style distributed caching.

## Prerequisite Lectures
- [[L07-CPU-Hardware-Branch-Prediction]] — Multicore architecture and cache hierarchy that cache coherency operates on

## Concepts Covered

- [[cache-coherency]]
- [[snoopy-caches]]
- [[write-through-cache]]
- [[write-back-cache]]
- [[msi-protocol]]
- [[mesi-protocol]]
- [[mesif-protocol]]
- [[false-sharing]]
- [[invalidation-vs-update]]
- [[distributed-cache-software]]
