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

# Fast Inverse Square Root

The fast inverse square root is a famous algorithm from Quake III Arena (attributed to John Carmack) that computes an approximation of 1/sqrt(x) in constant time. This operation is critical in graphics processing for normalizing vectors, which is needed for lighting and reflection calculations.

The trick works by reinterpreting the bits of a floating-point number as an integer, exploiting the fact that the IEEE 754 float layout (sign bit, exponent, mantissa) produces a value that roughly resembles -1/sqrt(x) when treated as an integer. A magic constant `0x5f3759df` is used as an offset to shift this approximation into the correct range. The result is then cast back to a float and refined with a single iteration of Newton's method, yielding an approximation with only about 0.175% error.

This is a textbook example of [[reduced-resource-computation]]: trading a tiny, imperceptible loss of accuracy for a fast constant-time calculation that replaces an expensive iterative square root computation. In a 1999 3D game, the visual difference was unnoticeable. Modern CPUs now include dedicated instructions for fast inverse square root, making the bit-hack less necessary, but the concept of using domain knowledge to find cheaper approximate calculations remains broadly applicable.

## Prerequisites

- [[reduced-resource-computation]] — Fast inverse square root is an instance of reduced-resource computation

## Lectures

- [[L14-Early-Termination-Reduced-Resource-Computation]]

## Related Concepts

- [[reduced-resource-computation]]
- [[early-phase-termination]]
