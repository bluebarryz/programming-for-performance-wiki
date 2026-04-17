---
tags:
  - concept
  - ece459
  - security
  - L07
prerequisites:
  - "[[cache-misses]]"
  - "[[hyperthreading]]"
---

# Side-Channel Attacks

Side-channel attacks exploit implementation details of hardware (rather than algorithmic weaknesses) to extract privileged data. In the context of ECE 459, two categories are covered:

**Cache attacks**: If an attacker can get memory loaded into the cache, they can extract it using a cache side-channel attack. The concept has been known for a while, but [[spectre-and-meltdown]] made it a major concern by showing how speculative execution can be used to load privileged memory into the cache.

**Hyperthreading attacks**: Since two threads sharing a core via [[hyperthreading]] share hardware resources, one thread can observe the other's behavior by timing its own cache accesses. Researchers demonstrated stealing a 384-bit secret key from another process this way. The only long-term fix may be preventing threads from different processes from sharing a core, or disabling hyperthreading entirely -- both with significant performance implications.

## Prerequisites

- [[cache-misses]] — Cache timing differences are the observation mechanism for cache side-channel attacks
- [[hyperthreading]] — Shared hardware resources between hyperthreads enable timing attacks

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[spectre-and-meltdown]]
- [[hyperthreading]]
- [[cache-misses]]
