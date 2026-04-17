---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[counters]]"
---

# Aggregate Measures

Aggregate measures are summaries of data derived from [[counters]] and other observations. The average response time of a request is a classic example: sum the total time per request, divide by the number of requests. Common aggregate measures include number of requests, requests broken down by type, average response time, and percentage of error responses.

Aggregate measures are only useful with context. An average login time of 0.75 seconds means nothing without a baseline to compare against. If it was 0.5 seconds before your PR, performance got worse. If the time limit is 1 second, you are within bounds; if the time limit is 10 seconds, there is plenty of room. The choice of time period matters too: looking at purchases per hour on Sunday night might be misleading compared to Monday at noon.

Averages can also be misleading. An average response time of 1.27 seconds does not preclude the possibility that some large percentage of requests exceed a 10-second deadline. To address this, use maximum and [[percentiles]] (like the 95th percentile). Averages also hide bursty behavior: 7 requests per second on average could be evenly distributed, or could come in bursts of 10 followed by empty periods.

## Prerequisites
- [[counters]] — Aggregate measures are derived from counter data

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[counters]]
- [[percentiles]]
- [[dashboards]]
- [[observability]]
