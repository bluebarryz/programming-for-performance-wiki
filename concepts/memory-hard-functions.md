---
tags:
  - concept
  - ece459
  - security
prerequisites:
  - "[[cryptographic-hashing]]"
  - "[[password-cracking]]"
---

# Memory-Hard Functions

A memory-hard algorithm on a Random Access Machine is one that uses S(n) space and T(n) operations, where S(n) is in the order of T(n)^(1-epsilon). In other words, the space required grows nearly as fast as the computation time. Memory-hard algorithms are expensive to implement in either hardware or software because they demand significant memory resources.

A sequential memory-hard function extends this concept: (1) the fastest sequential algorithm is memory-hard, and (2) it is impossible for a parallel algorithm to asymptotically achieve lower cost. This property is what makes scrypt effective for password hashing -- even with massive GPU parallelism, the memory requirements prevent attackers from gaining a significant advantage through parallelization. The memory cost means that custom hardware (like ASICs) cannot simply throw more compute units at the problem without also scaling memory proportionally, which is expensive.

## Prerequisites
- [[cryptographic-hashing]] — Memory-hard functions are a class of cryptographic hash functions
- [[password-cracking]] — Memory hardness counters GPU parallelism advantages in cracking

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[scrypt]]
- [[cryptographic-hashing]]
- [[password-cracking]]
- [[asic-miners]]
