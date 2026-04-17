---
tags:
  - lecture
  - ece459
  - hardware
  - branch-prediction
  - multicore
lecture: 7
title: CPU Hardware, Branch Prediction
date: 2024-09-10
prerequisite_lectures:
  - "[[L06-Modern-Processors]]"
---

# L07 - CPU Hardware, Branch Prediction

This lecture covers multicore processor hardware design (SMP, hyperthreading, NUMA) and dives deep into how branch prediction works, from the simplest static schemes to dynamic two-level adaptive predictors. It also discusses side-channel attacks (Spectre, Meltdown) that exploit speculative execution and their performance implications.

## Prerequisite Lectures
- [[L06-Modern-Processors]] — Pipelining, speculation, and branch prediction basics this lecture expands on

## Concepts Covered

- [[multicore-processors]]
- [[frequency-scaling]]
- [[symmetric-multiprocessing]]
- [[hyperthreading]]
- [[non-uniform-memory-access]]
- [[branch-prediction]]
- [[static-branch-prediction]]
- [[dynamic-branch-prediction]]
- [[two-bit-saturating-counter]]
- [[two-level-adaptive-predictor]]
- [[gshare-predictor]]
- [[branch-prediction-performance-model]]
- [[likely-unlikely-hints]]
- [[side-channel-attacks]]
- [[spectre-and-meltdown]]
