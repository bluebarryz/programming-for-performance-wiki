---
tags:
  - concept
  - ece459
  - security
  - gpu
prerequisites:
  - "[[data-parallelism]]"
  - "[[cuda]]"
---

# Password Cracking

Password cracking is a GPU application that demonstrates the massive parallelism of GPUs applied to a real-world problem. The fundamental approach is brute-force: each potential password is a point in the computation space, and the GPU computes hash values for all of them simultaneously. This maps perfectly to the data-parallel model of GPU computing.

Acceptable password storage practices require passwords to be hashed and salted using a cryptographic hash function -- never stored in plaintext. The first attack strategy is trying common passwords ("password", "system", etc.). If that fails, brute-force tries all possible passwords by computing hashes in parallel. Any website with basic security will lock accounts after too many failed attempts, but if an attacker obtains a copy of the hashed password database, brute-force becomes viable.

The arms race between crackers and defenders has historically focused on making the hash function more expensive to compute. Early UNIX passwords used repeated applications of the hash function to increase difficulty. The computational power available today is dramatically more than 20-30 years ago, so algorithms and key lengths must be updated regularly to stay ahead. Techniques like [[scrypt]] and [[rainbow-tables]] represent different approaches to this problem.

## Prerequisites
- [[data-parallelism]] — Brute-force password cracking maps perfectly to data-parallel GPU computation
- [[cuda]] — GPUs provide the massive parallelism needed for hash computation

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[cryptographic-hashing]]
- [[rainbow-tables]]
- [[scrypt]]
- [[memory-hard-functions]]
- [[bitcoin-mining]]
