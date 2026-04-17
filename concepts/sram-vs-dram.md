---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[memory-hierarchy]]"
---

# SRAM vs DRAM

**SRAM** (Static RAM) is the fast but expensive memory used for CPU caches. It uses six transistors per bit and does not need refreshing.

**DRAM** (Dynamic RAM) is the cheaper, slower memory used for main memory. It uses one transistor and one capacitor per bit. DRAM improvements have focused on bandwidth rather than latency -- DDR (Dual Data Rate) provides two transfers per cycle, but it still takes significant time to get data out. DRAM also needs periodic refreshes because capacitors leak charge.

The key performance insight is that DRAM speeds have not kept pace with CPU frequency improvements. CPU frequency doubled roughly every 2 years while DRAM speed doubled roughly every 6 years, creating a growing [[cpu-memory-gap]].

## Prerequisites

- [[memory-hierarchy]] — SRAM and DRAM are the technologies behind different levels of the hierarchy

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[memory-hierarchy]]
- [[cpu-memory-gap]]
- [[cache-misses]]
