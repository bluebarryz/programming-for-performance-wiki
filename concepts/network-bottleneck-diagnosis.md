---
tags:
  - concept
  - ece459
  - network
  - diagnostics
lectures:
  - L26
prerequisites:
  - "[[bottleneck-analysis]]"
  - "[[bandwidth-vs-latency]]"
---

# Network Bottleneck Diagnosis

Use `nload` to monitor current, average, min, max, and total network throughput. Tools like `speedtest.net` measure upload/download speed and latency to an external server, though this may not reflect the speed between your application and its specific backend.

Intermediary hardware (powerline adapters, wireless interference, old switches) can significantly reduce effective bandwidth below the theoretical maximum. **Packet loss** also cuts into effective bandwidth by requiring retransmissions.

Note that high bandwidth does not guarantee low latency -- the network could be bandwidth-rich but latency-poor (or vice versa).

## Prerequisites

- [[bottleneck-analysis]] — Network diagnosis is one step in systematic bottleneck analysis
- [[bandwidth-vs-latency]] — Understanding the distinction between bandwidth and latency is essential for network diagnosis

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[bottleneck-analysis]]
- [[network-latency-vs-bandwidth]]
