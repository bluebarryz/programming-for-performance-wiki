---
tags:
  - concept
  - ece459
  - performance
  - approximation
lectures:
  - L14
prerequisites:
  - "[[improving-latency]]"
---

# Reduced-Resource Computation

Reduced-resource computation is a performance strategy where accuracy or precision is intentionally decreased to speed up computation. Unlike [[early-phase-termination]] which skips entire tasks, reduced-resource computation does all the work but with less precision -- doing more with less.

The simplest form is using lower-precision data types: `float` instead of `double`, or even fewer than 8 bits as in Google's Tensor Processing Units. The appropriateness depends on the domain. In scientific simulations, measurements already have error and machine arithmetic introduces more, so the question is whether the simulation is "good enough." If circuit resistors have a tolerance of plus or minus 5%, computing their values to five decimal places is pointless.

The N-body problem is a concrete example. Beyond using `float` instead of `double`, domain knowledge enables further approximation: since gravitational force decreases with the square of distance, far-away bodies contribute negligible forces. By dividing space into bins, computing the centre of mass for each bin, and using exact force calculations only for nearby bins while approximating distant ones with centre-of-mass values, significant computation is saved. The [[fast-inverse-square-root]] from Quake III is another classic example: a bit-manipulation trick with one Newton's method iteration produces an approximation of 1/sqrt(x) with only 0.175% error in constant time.

## Prerequisites

- [[improving-latency]] — Reduced-resource computation trades precision for speed

## Lectures

- [[L14-Early-Termination-Reduced-Resource-Computation]]

## Related Concepts

- [[early-phase-termination]]
- [[loop-perforation]]
- [[fast-inverse-square-root]]
