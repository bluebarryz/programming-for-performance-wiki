---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[observability]]"
---

# Logging

Logging is the most recommended single tool for observing program execution. In production systems, logs typically include a timestamp, a message, and attributes. Logs have levels (error, warning, info, debug) that help filter relevant information. If only one observability tool is available, logging is the recommended choice because it reveals how much work the software did, when things are busy, which transactions are slow, and when services are down.

A typical approach logs incoming requests and outgoing responses with intermediate steps. Adding relevant attributes (like company IDs or operation types) helps correlate knowledge and identify patterns. Timestamps should use UTC to avoid daylight savings issues and cross-timezone confusion. The precision needed depends on the timescale of execution -- seconds for slow processes, microseconds or nanoseconds for fast ones.

The key balance is logging enough to be useful without logging so much that it becomes noisy, exposes PII, or causes significant overhead. Logs should always redact personally-identifiable information. Over-logging can happen when it becomes difficult to use other debugging tools, leading developers to log everything "just in case." Log aggregation services can help manage high-volume logs in real time.

## Prerequisites
- [[observability]] — Logging is the most fundamental observability tool

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[observability]]
- [[tracing]]
- [[counters]]
- [[dashboards]]
