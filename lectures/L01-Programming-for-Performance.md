---
tags:
  - lecture
  - ECE459
  - performance
lecture: L01
title: Programming for Performance
prerequisite_lectures: []
---

# L01 - Programming for Performance

This introductory lecture defines what "performance" means in the context of this course and establishes the two key metrics: bandwidth (items per unit time) and latency (time per item). It covers strategies for improving single-threaded latency (profiling, doing less work, caching, better algorithms, hardware upgrades), then motivates parallelism as a way to improve bandwidth. The lecture discusses difficulties with parallelism (dependencies, embarrassingly parallel problems, data races, deadlocks, stale data), introduces scalability, presents Crista's Five Laws of Performant Software, and explains why the course uses Rust.

## Prerequisite Lectures
None — this lecture is a starting point for the course.

## Concepts Covered

- [[bandwidth-vs-latency]]
- [[profiling]]
- [[improving-latency]]
- [[caching]]
- [[parallelism]]
- [[pipelining]]
- [[embarrassingly-parallel]]
- [[dependencies-in-parallelism]]
- [[data-races]]
- [[deadlocks]]
- [[scalability]]
- [[laws-of-performant-software]]
- [[amdahls-law]]
- [[rust-motivation]]
