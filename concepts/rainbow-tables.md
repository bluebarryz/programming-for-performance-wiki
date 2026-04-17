---
tags:
  - concept
  - ece459
  - security
  - gpu
prerequisites:
  - "[[cryptographic-hashing]]"
  - "[[password-cracking]]"
  - "[[data-parallelism]]"
---

# Rainbow Tables

Rainbow tables are a time-memory tradeoff for password cracking. Instead of brute-forcing every password from scratch, precomputed hash chains allow reuse of previous computations. The basic idea is to store mappings from hashes to passwords, but since storing every possible hash-plaintext pair is impractical, rainbow tables use a compromise involving "reduction" functions that map hashes back to plaintexts.

A chain is built by alternating hash and reduce operations: start with a plaintext, hash it, reduce the hash to a new plaintext, hash again, and repeat n times. Only the start and end points of each chain are stored. To crack a password given a hash: look for it in the list of final hashes, and if not found, reduce and re-hash to walk through the chain space until a match is found. Once the correct chain is identified, replay from the chain's starting plaintext to recover the original password.

Rainbow tables can be generated and searched efficiently on GPUs. Table generation on a GTX295 for MD5 proceeds at around 430M links/sec. The tables themselves are large (25-900 GB) but reusable forever for a given input set and hash function. They can even be downloaded from the internet. Both generation and lookup are embarrassingly parallel tasks well-suited to GPU computation.

## Prerequisites
- [[cryptographic-hashing]] — Rainbow tables precompute chains of hash values
- [[password-cracking]] — Rainbow tables are a time-memory tradeoff technique for cracking
- [[data-parallelism]] — Table generation and lookup are embarrassingly parallel GPU tasks

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[password-cracking]]
- [[cryptographic-hashing]]
- [[scrypt]]
