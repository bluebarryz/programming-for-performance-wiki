---
tags:
  - concept
  - ece459
  - devops
  - operations
lectures:
  - L35
prerequisites:
  - "[[incident-reports]]"
---

# Root Cause vs Proximate Cause

When analyzing why an incident happened, there are two kinds of causes: root causes and proximate causes. Proximate causes are the things that happen just before the problem or are the immediate trigger. Root causes are the deeper, underlying reasons why the problem was possible in the first place.

The lecture uses a deadlock example to illustrate the distinction. A deadlock occurs because thread A acquires lock X then waits for lock Y, while thread B locks Y then waits for X. The proximate cause might be "User 1 tried to update a record while User 2 was running a report," which triggered the conflicting lock acquisitions. But the root cause is that the code does not always acquire locks in a consistent order.

It is critical to focus on finding the root cause rather than stopping at the superficial level. Saying "I wrote a bug" and concluding "write more tests" is part of the solution but does not go far enough. Root causes might include unrepresentative test environments, lack of knowledge about concurrency, or missing deployment stages. The [[five-whys]] technique helps drill down to the appropriate level of root cause analysis.

## Prerequisites

- [[incident-reports]] — Root cause analysis is a key component of writing effective incident reports

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[five-whys]]
- [[incident-reports]]
- [[devops]]
