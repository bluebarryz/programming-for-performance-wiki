---
tags:
  - concept
  - ece459
  - disk
  - diagnostics
lectures:
  - L26
prerequisites:
  - "[[bottleneck-analysis]]"
  - "[[memory-hierarchy]]"
---

# Disk Bottleneck Diagnosis

Use `iostat -dx <device> <interval>` to check disk utilization. The key column is **%util** -- if it is near 100%, the disk is the bottleneck. To see which processes are consuming I/O, use `iotop` (requires root).

Even if memory is not the bottleneck, the disk could still be limiting performance due to direct I/O operations (e.g., database reads, file processing). Checking disk is a natural follow-up after ruling out memory/swap issues.

## Prerequisites

- [[bottleneck-analysis]] — Disk diagnosis is one step in systematic bottleneck analysis
- [[memory-hierarchy]] — Understanding that disk is the slowest tier explains why disk bottlenecks are severe

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[bottleneck-analysis]]
- [[swap-and-paging]]
- [[memory-bottleneck-diagnosis]]
