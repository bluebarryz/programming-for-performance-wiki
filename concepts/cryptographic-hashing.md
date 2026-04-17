---
tags:
  - concept
  - ece459
  - security
prerequisites: []
---

# Cryptographic Hashing

A cryptographic hash function is a one-way function where the forward direction (computing the hash) is easy, but the inverse (recovering the input from a hash) is computationally hard. Instead of storing plaintext passwords, systems store hashes. Examples include SHA-3 and scrypt. Some older algorithms like DES and SHA1 are considered broken and offer essentially no security.

The strength of a cryptographic hash depends on both the algorithm choice and the implementation. Even a good algorithm with no known vulnerabilities can be undermined by a broken implementation or insufficient bit length (e.g., using 32 bits instead of 512). The one-way property means that even if an attacker obtains the hash database, they cannot directly reverse the hashes to recover passwords. However, they can attempt brute-force attacks by computing hashes of candidate passwords and comparing results, which is where GPU parallelism becomes relevant.

## Prerequisites
None — foundational concept.

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[password-cracking]]
- [[scrypt]]
- [[rainbow-tables]]
- [[memory-hard-functions]]
- [[bitcoin-mining]]
