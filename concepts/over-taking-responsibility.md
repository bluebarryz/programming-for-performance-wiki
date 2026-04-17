---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[system-design]]"
  - "[[architectural-bottlenecks]]"
---

# Over-Taking Responsibility

Over-taking responsibility is a software architecture anti-pattern where a component does work that would be more efficiently handled by another part of the system. A classic example is fetching an entire database table into application memory and then searching and filtering it there, instead of letting the database server handle the filtering. The database has more information -- indexes, data layout on disk, query optimization -- and can perform the work far more efficiently.

Another form is the backend doing work better suited for the frontend. Rendering pages server-side was once the norm, but moving rendering to the frontend or mobile app reduces backend load. The reverse also applies: the backend must still validate all input from the frontend, since it cannot trust client-side data.

Over-taking responsibility often arises from organizational or technical constraints. Gatekeeping, the remote server being run by another company, or slow procurement processes may make it faster to do the work yourself even though it is inefficient. This tends to result in painful change management and high tech debt, especially when people become afraid of touching a critical but fragile system. While no software architecture can solve organizational problems, awareness of the pattern helps identify where performance is being lost and where negotiation or intermediary systems could help.

## Prerequisites

- [[system-design]] — Over-taking responsibility is a system design anti-pattern
- [[architectural-bottlenecks]] — Components that over-take responsibility often become bottlenecks

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[system-design]]
- [[architectural-bottlenecks]]
- [[excessive-network-calls]]
