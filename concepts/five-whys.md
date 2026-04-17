---
tags:
  - concept
  - ece459
  - devops
  - operations
lectures:
  - L35
prerequisites:
  - "[[root-cause-vs-proximate-cause]]"
  - "[[incident-reports]]"
---

# Five Whys

The Five Whys is a root cause analysis technique originating from Toyota. The idea is to ask "why?" repeatedly (approximately five times) to drill past superficial explanations and reach the actual root cause of an incident. It serves as a guide to finding the right level of analysis.

If you do not ask "why?" enough times, your answers remain too superficial -- for example, stopping at "I wrote a bug" and concluding "don't do that, write more tests." Those are part of the solution but do not go far enough. You also need to consider deeper causes like unrepresentative test environments or lack of knowledge about a particular subject (e.g., concurrency).

Conversely, if you ask "why?" too many times, you end up at absurdly general conclusions like "writing code is hard" or "computers were a mistake." The goal is to find the sweet spot where the root cause is specific enough to be actionable but deep enough to prevent recurrence. This technique is a core part of writing effective [[incident-reports]].

## Prerequisites

- [[root-cause-vs-proximate-cause]] — The Five Whys technique drills past proximate causes to find root causes
- [[incident-reports]] — Five Whys is used when writing incident reports to find the right depth of analysis

## Lectures

- [[L35-DevOps-Operations]]

## Related Concepts

- [[incident-reports]]
- [[root-cause-vs-proximate-cause]]
- [[devops]]
