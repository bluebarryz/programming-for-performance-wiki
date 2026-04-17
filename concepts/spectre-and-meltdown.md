---
tags:
  - concept
  - ece459
  - security
  - L07
prerequisites:
  - "[[speculation]]"
  - "[[branch-prediction]]"
  - "[[cache-misses]]"
  - "[[side-channel-attacks]]"
---

# Spectre and Meltdown

Spectre and Meltdown are attacks disclosed in early 2018 that leverage speculative execution to break process isolation guarantees. In principle, a process should not be able to read memory belonging to the kernel or other processes. These attacks violate that principle.

**How Spectre (variant 2) works**: At a branch, the CPU speculatively executes the predicted path. Attack code trains the branch predictor to mispredict, causing the CPU to speculatively execute attacker-chosen code. This speculative code reads secret data (e.g., from the kernel) and loads it into the cache. Even though the speculative execution is rolled back, the cache state change persists and can be observed through timing measurements.

**Meltdown** works similarly but exploits out-of-order execution to read kernel memory directly before the permission check completes.

The mitigations involve additional security measures in both hardware and software, which unfortunately result in lower performance. This is a case where performance optimizations ([[speculation]], [[branch-prediction]]) created security vulnerabilities.

## Prerequisites

- [[speculation]] — Spectre and Meltdown exploit speculative execution to read privileged memory
- [[branch-prediction]] — Spectre trains the branch predictor to mispredict, triggering speculative reads
- [[cache-misses]] — The leaked data is observed through cache timing side-channels
- [[side-channel-attacks]] — Spectre/Meltdown are specific instances of cache side-channel attacks

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[side-channel-attacks]]
- [[speculation]]
- [[branch-prediction]]
- [[cache-misses]]
