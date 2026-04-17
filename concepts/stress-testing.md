---
tags:
  - concept
  - ece459
  - testing
prerequisites:
  - "[[load-testing]]"
---

# Stress Testing

Stress testing is distinct from [[load-testing]]. Load testing has a specific target and aims to demonstrate the application can handle that amount. Stress testing turns up the pressure (load) until things break or stop working well -- finding the "ultimate breaking strain" of the system.

The course does not go into stress testing in depth, but notes that the load testing techniques can be repurposed for stress testing by simply increasing the numbers. The goal is different: instead of "can we handle X?", stress testing asks "at what point does the system fail?" This is useful for understanding system limits and planning capacity.

## Prerequisites
- [[load-testing]] — Stress testing extends load testing by increasing pressure until failure

## Lectures

- [[L25-Load-Testing]]

## Related Concepts

- [[load-testing]]
- [[endurance-testing]]
- [[evaluating-load-test-success]]
