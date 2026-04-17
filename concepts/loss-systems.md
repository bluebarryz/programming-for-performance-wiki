---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[kendall-notation]]"
  - "[[mmk-queue]]"
  - "[[balking]]"
---

# Loss Systems

A loss system is one where service is refused because of capacity limits. The concept originates from early telephone systems: there were k circuits, and if none of the k circuits was free when a person wanted to make a call, the call was simply dropped (it failed). In queueing theory notation, this is an M/M/k/k system -- a system with k servers and a buffer size of k (no waiting room).

In the food hall or Service Ontario context, loss occurs when the building reaches capacity. If the building is full, you are turned away by security and not allowed to queue, no matter how badly you want the service. Unlike [[balking]] (choosing not to enter) or [[reneging]] (leaving after entering), loss is enforced by the system itself.

Loss systems are important in performance modeling because they represent hard capacity constraints. In computing, a router dropping packets when its buffer is full is a classic example of a loss system. The probability of loss (and therefore the fraction of demand that goes unserved) is a key metric for designing such systems.

## Prerequisites

- [[kendall-notation]] — Loss systems use M/M/k/k notation with finite buffer size
- [[mmk-queue]] — Loss systems extend the M/M/k model by adding a hard capacity constraint
- [[balking]] — Loss differs from balking: it is system-enforced refusal rather than customer choice

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[balking]]
- [[reneging]]
- [[priority-queuing]]
