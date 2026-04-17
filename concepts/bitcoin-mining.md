---
tags:
  - concept
  - ece459
  - gpu
  - security
prerequisites:
  - "[[cryptographic-hashing]]"
  - "[[cuda]]"
---

# Bitcoin Mining

Bitcoin is "mined" by performing hash computations, specifically SHA-256. In the early days, CPUs could mine Bitcoin, but as the difficulty of completing each unit of work increases periodically, CPUs quickly became too inefficient. GPUs were the logical next step due to their massive parallelism for hash computation.

When even GPU mining was insufficient, miners turned to custom hardware. The calculations needed are limited to cryptographic hashing operations (and, xor, rotate, add, modulo, right shift) in a fixed order, so specialized circuits can be designed. The first hardware miners used FPGAs, but these were quickly replaced by [[asic-miners]], which are far more efficient in both hashes per second and power consumption. As more mining hardware comes online, the difficulty increases, making it essentially impossible to profit with older hardware.

The environmental cost is significant: at the time of the lecture, Bitcoin's carbon footprint was comparable to the country of Uzbekistan, and its electricity consumption was comparable to Poland's entire power consumption. The conclusion from a performance perspective is clear: don't mine Bitcoin -- the difficulty is high, hardware costs are significant, power is not free, and new technology constantly makes existing rigs obsolete.

## Prerequisites
- [[cryptographic-hashing]] — Bitcoin mining is fundamentally SHA-256 hash computation
- [[cuda]] — GPUs were the second generation of mining hardware after CPUs

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[cryptographic-hashing]]
- [[asic-miners]]
- [[password-cracking]]
