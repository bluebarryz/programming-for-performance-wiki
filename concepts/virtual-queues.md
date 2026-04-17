---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[priority-queuing]]"
  - "[[balking]]"
  - "[[reneging]]"
---

# Virtual Queues

A virtual queue is one where the customer does not have to physically stand in line while waiting. Instead, they receive a ticket or reservation that specifies a return time, and they can do something else in the meantime. The queue still exists logically, but the customer is freed from physically occupying a spot in it.

In the [[fastpass-case-study]], the FastPass system is a virtual queue: instead of standing in line for a popular ride, a person gets a ticket with a return time. While waiting, they can visit less popular attractions, get food, or do other activities. This does not reduce their wait in the virtual queue -- they wait just as long as they would in the physical line -- but it allows them to use that time productively.

The FastPass++ system takes virtual queues further toward a reservation model, where guests select priority passes for specific attractions in advance (or on arrival). These passes can sell out if demand is sufficient. The simulation results show that virtual queues encourage better utilization of less popular services and increase overall activity, even though standby wait times increase for those not using the virtual queue system.

## Prerequisites

- [[priority-queuing]] — Virtual queues implement priority by giving some customers reserved return times
- [[balking]] — Virtual queues reduce balking by freeing customers from physically standing in line
- [[reneging]] — Virtual queues reduce reneging by letting customers do other things while waiting

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[fastpass-case-study]]
- [[priority-queuing]]
- [[balking]]
- [[reneging]]
