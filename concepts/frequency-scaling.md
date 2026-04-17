---
tags:
  - concept
  - ece459
  - hardware
  - L06
  - L07
prerequisites: []
---

# Frequency Scaling

Between 1985 and 2005, CPU clock speeds grew dramatically -- from ~10 MHz to ~3 GHz. Higher clock speed means more cycles per second, which means more work done per second. This era of frequency scaling made performance improvement straightforward: next year's CPU would simply be faster.

Around 2005, clock speeds hit a wall at roughly 3 GHz. Going faster requires more voltage, which means more power and more heat. More heat leads to higher failure rates, and cooling itself takes power. This "power wall" is the fundamental reason the industry shifted to multicore processors instead of continuing to increase clock speeds.

Modern Intel and AMD chips support burst speeds above the base clock rate, but the base rate has not substantially increased beyond ~3 GHz in recent decades.

## Prerequisites

None — foundational concept.

## Lectures

- [[L06-Modern-Processors]]
- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[multicore-processors]]
- [[instruction-level-parallelism]]
- [[pipelining]]
