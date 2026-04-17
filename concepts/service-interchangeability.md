---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[multiple-services]]"
---

# Service Interchangeability

Service interchangeability describes the degree to which different services or servers can substitute for one another. It exists on a spectrum: total interchangeability, partial interchangeability, and no interchangeability at all.

Total interchangeability means the requester does not care which service they get -- in the food hall example, you are so hungry that tacos, pizza, or shawarma would all satisfy you equally. Partial interchangeability means you have preferences but would accept alternatives under certain circumstances -- you want tacos but would accept shawarma if the taco line is too long. No interchangeability means you will accept nothing else -- you are set on pizza and will wait no matter what.

Whether things are interchangeable depends on both the nature of the services and the needs of the requester. At Service Ontario, renewing a driver's license and getting a new health card are completely non-interchangeable -- you cannot substitute one for the other. Similarly, if someone is a vegan, the taco stand might be their only option regardless of other queue lengths. In computing, this maps to whether different servers or microservices can handle the same types of requests.

## Prerequisites

- [[multiple-services]] — Interchangeability describes the degree to which different services can substitute for each other

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[multiple-services]]
- [[cattle-not-pets]]
- [[maintenance-and-downtime]]
