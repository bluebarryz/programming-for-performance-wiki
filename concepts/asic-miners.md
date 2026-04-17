---
tags:
  - concept
  - ece459
  - gpu
prerequisites:
  - "[[bitcoin-mining]]"
  - "[[cryptographic-hashing]]"
---

# ASIC Miners

ASIC (Application-Specific Integrated Circuit) miners are custom hardware designed exclusively for cryptographic hashing. Unlike general-purpose CPUs or GPUs, they implement only the few operations needed for hash computation (and, xor, rotate, add, modulo, right shift) in a fixed order, eliminating all unnecessary functionality.

ASIC miners replaced FPGA-based miners in Bitcoin mining and are far more efficient in both hashes computed per second and power consumption. However, they represent an escalation in the mining arms race: as more ASICs come online, the mining difficulty increases, making it progressively harder to mine with existing hardware. The constant release of newer, more efficient ASICs means that a mining rig's profitability window shrinks rapidly. Combined with significant upfront hardware costs and ongoing power consumption, this makes Bitcoin mining a losing proposition for most participants.

## Prerequisites
- [[bitcoin-mining]] — ASICs replaced GPUs and FPGAs in the Bitcoin mining arms race
- [[cryptographic-hashing]] — ASICs implement only the specific hash operations needed

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[bitcoin-mining]]
- [[cryptographic-hashing]]
