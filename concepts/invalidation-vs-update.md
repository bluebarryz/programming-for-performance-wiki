---
tags:
  - concept
  - ece459
  - cache
lectures:
  - "08"
prerequisites:
  - "[[cache-coherency]]"
---

# Invalidation vs Update

When a cache coherency protocol detects that a cached value has been modified by another processor, it must take one of two actions: invalidation or update. Invalidation marks the stale copy as invalid, so the next access will fetch the current value from memory or another cache. Update (also called write broadcast) pushes the new value to all caches that hold a copy.

Invalidation is the most common approach in hardware. It uses less bus bandwidth because it only sends a short "this is invalid" signal rather than the full data. The downside is that the next read of the invalidated data will cause a cache miss, requiring a fetch from memory or another cache. Update avoids this subsequent miss by proactively distributing the new value, but at the cost of higher bandwidth usage for every write to shared data -- even if no other cache will read that value again soon.

The lecture illustrates these two approaches with a travel analogy: Air Canada sent an update ("departure time revised to 22:00") while Deutsche Bahn sent an invalidation ("something changed; check the app"). Both approaches ensure the recipient eventually gets correct information, but the user experience and efficiency differ. In hardware, the choice is made by the chip designers. In software distributed caches, the developer gets to choose which strategy best fits their access patterns.

## Prerequisites

- [[cache-coherency]] — Invalidation and update are the two fundamental actions a coherency protocol can take

## Lectures
- [[L08-Cache-Coherency]]

## Related Concepts
- [[cache-coherency]]
- [[snoopy-caches]]
- [[write-through-cache]]
- [[write-back-cache]]
