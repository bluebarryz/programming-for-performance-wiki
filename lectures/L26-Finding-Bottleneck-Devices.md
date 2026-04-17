---
tags:
  - lecture
  - ece459
  - profiling
  - bottlenecks
  - performance
lecture: 26
title: Finding Bottleneck Devices
date: 2025-12-31
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
  - "[[L06-Modern-Processors]]"
---

# L26 - Finding Bottleneck Devices

Before diving into CPU profiling, this lecture stresses the importance of first identifying which resource is actually the bottleneck. The five main culprits are CPU, memory, disk, network, and locks. Tools like `top`, `vmstat`, `iostat`, `nload`, and `traceroute` are introduced for diagnosing each. The lecture also warns that what looks like a performance problem may actually be a programming error (e.g., blocking the UI thread), and that sometimes the correct answer is simply that the user needs better hardware.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Need performance concepts and profiling motivation
- [[L06-Modern-Processors]] — Need memory hierarchy understanding for memory/cache bottlenecks

## Concepts Covered

- [[bottleneck-analysis]]
- [[cpu-load-average]]
- [[memory-bottleneck-diagnosis]]
- [[swap-and-paging]]
- [[disk-bottleneck-diagnosis]]
- [[network-bottleneck-diagnosis]]
- [[network-latency-vs-bandwidth]]
- [[lock-contention-diagnosis]]
- [[cpu-profiling]]
