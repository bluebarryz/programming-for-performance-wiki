---
tags:
  - concept
  - ece459
  - security
prerequisites:
  - "[[cryptographic-hashing]]"
  - "[[password-cracking]]"
---

# Scrypt

Scrypt is a password hashing technique (also the algorithm behind DogeCoin) designed to make brute-force cracking expensive in both time and space. The main idea is to force the use of the "most memory possible" for a given number of operations, increasing both the number of operations and the cost of brute-forcing.

Scrypt is built on the concept of [[memory-hard-functions]]. More memory implies more circuitry required to implement the algorithm, making it expensive in both hardware and software. The scrypt paper exhibits ReMix as a concrete example of a sequential memory-hard function, and concludes with BlockMix as a hard function in a cache-aware model. The difficulty can be tuned so that computing a single password hash remains reasonable for a legitimate user, but trying all possible passwords becomes intractable with current hardware.

## Prerequisites
- [[cryptographic-hashing]] — Scrypt is a specific cryptographic hash designed to resist brute-force attacks
- [[password-cracking]] — Scrypt exists as a defense against GPU-accelerated password cracking

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[memory-hard-functions]]
- [[cryptographic-hashing]]
- [[password-cracking]]
- [[bitcoin-mining]]
