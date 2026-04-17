---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[branch-prediction]]"
  - "[[pipelining]]"
  - "[[static-branch-prediction]]"
  - "[[dynamic-branch-prediction]]"
---

# Branch Prediction Performance Model

The course presents a "cartoon model" for quantifying the performance impact of branch prediction. Assumptions:

- The CPU executes 1 instruction per clock on average
- Mispredicted branches cost 20 cycles; correct predictions cost 1 cycle
- The instruction mix is 80% non-branches and 20% branches

The formula for average cycles per instruction:

```
CPI = non_branch% * 1 + (accuracy * branch%) * 1 + ((1 - accuracy) * branch%) * 20
```

Results across prediction schemes:

| Scheme | Accuracy | CPI |
|--------|----------|-----|
| No prediction | 0% | 4.8 |
| Predict taken | 70% | 2.14 |
| BTFNT | 80% | 1.76 |
| 1-bit dynamic | 85% | 1.57 |
| 2-bit saturating | 90% | 1.38 |
| Two-level global | 93% | 1.27 |
| Two-level local | 94% | 1.23 |
| Perfect | 100% | 1.0 |

Perfect branch prediction would make code run 4.8x faster than no prediction. Even the simplest dynamic scheme gets most of the benefit. This is an application of expected value computation to predict performance.

## Prerequisites

- [[branch-prediction]] — The model quantifies the performance impact of prediction accuracy
- [[pipelining]] — The misprediction penalty depends on pipeline depth
- [[static-branch-prediction]] — The model compares static scheme accuracies
- [[dynamic-branch-prediction]] — The model compares dynamic scheme accuracies

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[branch-prediction]]
- [[static-branch-prediction]]
- [[dynamic-branch-prediction]]
- [[pipelining]]
