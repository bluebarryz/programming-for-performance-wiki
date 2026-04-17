---
tags:
  - concept
  - ece459
  - cache
  - hardware
lectures:
  - "08"
prerequisites:
  - "[[msi-protocol]]"
---

# MESI Protocol

MESI is the most common cache coherency protocol, extending the [[msi-protocol]] with a fourth state: Exclusive. The four states are:

- **Modified** -- only this cache has a valid copy; main memory is out-of-date.
- **Exclusive** -- only this cache has a valid copy; main memory is up-to-date.
- **Shared** -- the location is unmodified, consistent with main memory, and may exist in other caches.
- **Invalid** -- the cached copy is not valid.

The key advantage of the Exclusive state is that a processor can transition from Exclusive to Modified without any bus communication, since no other cache holds the data. In the [[msi-protocol]], even when only one cache has a copy, a write still requires a BusRdX to announce exclusive ownership. MESI eliminates this unnecessary bus traffic, reducing contention and improving performance.

MESI is safe because the Exclusive state guarantees that no other processor has the data. The protocol is used in real hardware and also serves as the basis for the distributed software cache implementation discussed in L08, where nodes track item states and use invalidation messages to maintain coherency.

## Prerequisites

- [[msi-protocol]] — MESI extends MSI with the Exclusive state to reduce unnecessary bus traffic

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[cache-coherency]]
- [[msi-protocol]]
- [[mesif-protocol]]
- [[false-sharing]]
- [[distributed-cache-software]]
