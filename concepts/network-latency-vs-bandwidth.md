---
tags:
  - concept
  - ece459
  - network
  - latency
lectures:
  - L26
prerequisites:
  - "[[bandwidth-vs-latency]]"
---

# Network Latency vs Bandwidth

A network connection can have high bandwidth but still be slow due to latency. The lecture gives the example of users in Hong Kong experiencing slowness when the backend is deployed in Frankfurt -- the problem is not bandwidth but the round-trip time for packets.

`traceroute` shows the path packets take and the latency at each hop. Communication latency can never be fully eliminated because of the speed of light in fibre-optic cable (real-world measurements show about 84% of lightspeed in fibre) and processing time at each network device along the path.

## Prerequisites

- [[bandwidth-vs-latency]] — The general latency vs bandwidth distinction from L01 applies directly to network performance

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[network-bottleneck-diagnosis]]
- [[bottleneck-analysis]]
