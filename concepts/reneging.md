---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[balking]]"
  - "[[queueing-theory]]"
---

# Reneging

Reneging is what happens when a customer enters a queue but gives up and leaves before reaching the front. Unlike [[balking]] (never entering the queue), reneging means the customer was in the queue and decided the wait was not worth it. In the food hall example, you join the taco line but leave because it is taking too long and you are too hungry to wait.

Reneging can also occur due to external constraints rather than pure impatience. At Service Ontario, you might leave because your lunch break is ending and you need to go back to work, even if you would otherwise be willing to wait. The decision to renege is based on an ongoing reassessment of the expected remaining wait versus the value of the service.

In both [[balking]] and reneging, there is an implicit or explicit estimate of the waiting time. The initial estimate when entering the queue can turn out to be wrong -- perhaps the service time was longer than expected, or the line was longer than it appeared. People cutting in line (priority customers) can also invalidate the estimate, as the wait grows longer than anticipated, potentially triggering a decision to renege.

## Prerequisites

- [[balking]] — Reneging is the in-queue counterpart to balking (leaving vs never joining)
- [[queueing-theory]] — Reneging complicates basic queueing models by allowing customers to leave mid-wait

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[balking]]
- [[loss-systems]]
- [[priority-queuing]]
- [[virtual-queues]]
