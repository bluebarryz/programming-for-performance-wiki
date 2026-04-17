---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[bandwidth-vs-latency]]"
---

# Scalability

Performance is important, but scalability is also a concern: the trend of performance with increasing load. A program generally has a designed load (e.g., x transactions per hour). A properly designed program will meet this intended load. If performance deteriorates rapidly with increasing load, we say it is *not scalable*.

This is undesirable, and for the most part if we have a good program design it can be fixed. If we have a bad program design, then no amount of performance techniques are going to help ("rearranging deck chairs on the Titanic").

The course focuses on ways to meet x or even raise x. Even the most scalable systems have limits, and while higher is better, nothing is infinite.

## Prerequisites
- [[bandwidth-vs-latency]] — Scalability describes how performance metrics change under increasing load

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[bandwidth-vs-latency]]
- [[parallelism]]
- [[laws-of-performant-software]]
