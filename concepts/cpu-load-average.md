---
tags:
  - concept
  - ece459
  - cpu
  - diagnostics
lectures:
  - L26
prerequisites:
  - "[[bottleneck-analysis]]"
---
			
# CPU Load Average

The `top` command on Linux reports one-minute, five-minute, and fifteen-minute load averages. These indicate how many processes are waiting for CPU time. The bridge/traffic analogy helps interpret them for a single core:

- **0.00 -- 0.99**: under capacity, no delays
- **1.00**: exactly at capacity
- **Above 1.00**: backup/delay (e.g., 2.00 means the core is full and an equal number of processes are waiting)

For multi-core systems, divide the load by the number of cores. A load of 3.00 on a quad-core CPU is equivalent to 0.75 on a single core (75% utilization).

Rules of thumb: above 0.70 warrants investigation, consistently at 1.00 is a serious problem, and 5.00 is a red alert.

## Prerequisites

- [[bottleneck-analysis]] — Load averages are one diagnostic within the broader bottleneck analysis framework

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[bottleneck-analysis]]
- [[cpu-profiling]]
