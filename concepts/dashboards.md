---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[aggregate-measures]]"
  - "[[counters]]"
---

# Dashboards

Dashboards are collections of useful graphs (time trends, histograms, etc.) that present an easily-digestible summary of system behavior. They are more than just pretty pictures of "LINE GOES UP" -- good dashboards make it clear what is happening and what needs attention.

Visualization is important because it reveals trends that raw numbers obscure. Digital speedometers are more precise, but analog speedometers make rate of change easier to perceive. Graphs of data over time make it easier to identify trends or alarming changes, and managers and non-technical people find them accessible. Dashboards make the most sense when monitoring many things (like a production system), and less sense when optimizing a single specific operation. They are a natural complement to [[aggregate-measures]] and [[counters]].

## Prerequisites
- [[aggregate-measures]] — Dashboards visualize aggregate measures and counter data
- [[counters]] — Counters provide the underlying data that dashboards display

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[aggregate-measures]]
- [[counters]]
- [[observability]]
- [[logging]]
