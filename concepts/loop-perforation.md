---
tags:
  - concept
  - ece459
  - performance
  - approximation
lectures:
  - L14
prerequisites:
  - "[[reduced-resource-computation]]"
---

# Loop Perforation

Loop perforation is a technique for speeding up sequential programs by skipping loop iterations. Instead of executing every iteration, the loop step size is increased and the final result is scaled to compensate. For example, a summation loop `for i in 0..n` can be changed to `for i in (0..n).step_by(2)` with the result multiplied by 2, yielding a 2x speedup.

This only produces acceptable results when the input data is appropriately distributed -- the sampled iterations must be representative of the skipped ones. The technique is a form of [[reduced-resource-computation]] applied at the loop level rather than at the task level.

Research by Rinard et al. demonstrates that loop perforation works well in domains like evaluating forces on water molecules, Monte Carlo simulation for swaption pricing, and video encoding. In the video encoding case, changing loop increments from 4 to 8 gave a 1.67x speedup with only a 0.87% decrease in signal-to-noise ratio and an 18.47% increase in bitrate, producing visually indistinguishable results.

## Prerequisites

- [[reduced-resource-computation]] — Loop perforation is a form of reduced-resource computation applied to loops

## Lectures

- [[L14-Early-Termination-Reduced-Resource-Computation]]

## Related Concepts

- [[reduced-resource-computation]]
- [[early-phase-termination]]
