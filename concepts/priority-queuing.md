---
tags:
  - concept
  - ece459
  - queueing-theory
lectures:
  - L33
prerequisites:
  - "[[queueing-theory]]"
  - "[[multiple-services]]"
---

# Priority Queuing

Priority queuing allows some customers or requests to be served before others, regardless of arrival order. The lecture uses the example of an elderly person with mobility restrictions being allowed to go to the front of the queue at Service Ontario -- it is sensible because asking them to stand in a very long line is not kind.

Priority introduces interesting effects and trade-offs. Key questions include: how much does priority help the prioritized group? How much does it disadvantage the non-prioritized group? Can the priority system incentivize people to choose less popular options? And critically, if everyone has priority, nobody has priority -- so how many requests can receive priority before the benefit is lost?

The [[fastpass-case-study]] explores these questions through simulation. In the Disney theme park setting, there are two queues for each ride: the priority queue (fast lane) and the standby queue. The ratio of priority to standby guests varies from about 4:1 under normal conditions to as high as 100:1 during peak times. The simulation shows that priority systems can increase overall utilization and ride counts, but they also introduce inequality among guests.

## Prerequisites

- [[queueing-theory]] — Priority queuing modifies the standard FIFO assumption in queueing models
- [[multiple-services]] — Priority systems interact with multiple services by redistributing demand

## Lectures

- [[L33-More-Advanced-Queueing-Theory]]

## Related Concepts

- [[fastpass-case-study]]
- [[virtual-queues]]
- [[balking]]
- [[reneging]]
