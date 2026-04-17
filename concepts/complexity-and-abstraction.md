---
tags:
  - concept
  - ece459
  - software-architecture
lectures:
  - "10"
prerequisites:
  - "[[system-design]]"
---

# Complexity and Abstraction

Complexity is the enemy of performance. In software architecture, unnecessary complexity often results from copying the practices of large industry leaders without understanding that those choices are relevant for their scale, not yours. This cargo-culting creates over-engineered systems with more services, more layers, and more data movement -- all of which slow things down.

Some complexity is inherent and unavoidable (e.g., tax software must implement every rule in the tax code). The dangerous kind is accidental complexity introduced by developers through excessive patterns, factory classes, and layers of indirection. David J. Wheeler's saying -- "We can solve any problem by introducing an extra level of indirection" -- is sometimes treated as gospel, but every layer of indirection adds overhead, can duplicate work, and slows development. The course advises using as much abstraction as necessary and no more.

"Architecture astronauts" -- people who design systems without writing code -- tend to encourage over-engineering and overly complex solutions. More services and layers means more data movement, and longer communication chains are slower than shorter ones. The practical advice is to minimize non-essential complexity, resist the urge to prematurely adopt patterns designed for much larger scales, and let the actual needs of the system drive the architecture.

## Prerequisites

- [[system-design]] — Complexity is a system design concern that affects performance at every level

## Lectures
- [[L10-Software-Architecture]]

## Related Concepts
- [[system-design]]
- [[monolith-vs-microservices]]
- [[architectural-bottlenecks]]
