---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[queueing-theory]]"
  - "[[load-balancing]]"
---

# Multiple Services

In basic queueing models, all servers provide the same service and every server can handle every kind of request. In reality, systems often have multiple distinct services. The lecture uses the food hall analogy: a food hall has many counter-service restaurants offering different cuisines. You cannot get tacos from the gelato stand.

This means that a customer must queue for the specific service they want, even if other queues are shorter or empty. The Mexican restaurant may have an extremely long line because of its excellent tacos, while the gelato stand has no queue at all. Unlike the simple model where any server can serve any customer, here the services are specialized and queues are independent.

Service Ontario provides a contrasting example where a single queue feeds multiple interchangeable servers -- any staff member can handle a driver's license renewal, health card renewal, or vehicle registration. Whether services are interchangeable depends on both the nature of the services and the needs of the people requesting them, which is captured by the concept of [[service-interchangeability]].

## Prerequisites

- [[queueing-theory]] — Multiple services extend basic queueing models beyond identical-server assumptions
- [[load-balancing]] — Contrasts with load balancing where any server can handle any request

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[service-interchangeability]]
- [[maintenance-and-downtime]]
- [[priority-queuing]]
