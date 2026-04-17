---
tags:
  - concept
  - ece459
  - testing
prerequisites:
  - "[[load-testing]]"
---

# Endurance Testing

Endurance testing maintains load over an extended period to catch problems that only emerge over time. The running analogy illustrates this: running at 10 km/h for 1 minute is easy, 30 minutes is manageable, but 4 hours causes fatigue and breakdown. Software experiences similar "fatigue" through memory leaks, filling up disk, exhausting file handles, growing log length, or accumulated errors.

This is not hypothetical: the course instructor describes services that hit internal resource limits during holiday-season code freezes, requiring instance-by-instance restarts. The question of how long to run an endurance test has no universal answer. Product requirements provide a first guide -- an e-commerce platform might target the period from Thanksgiving through Cyber Monday (five days). Maintenance windows also matter: if SLAs allow downtime from 02:00-03:00 on Sundays, the test should verify the system runs correctly between those windows.

Success in endurance testing is not just "can the system handle load X?" but "can it continue to handle load X consistently over a long period?" The trend over time may be more instructive than a single pass/fail result.

## Prerequisites
- [[load-testing]] — Endurance testing is load testing sustained over an extended period

## Lectures

- [[L25-Load-Testing]]

## Related Concepts

- [[load-testing]]
- [[stress-testing]]
- [[evaluating-load-test-success]]
- [[constant-vigilance]]
