---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[branch-prediction]]"
  - "[[pipelining]]"
---

# Static Branch Prediction

Static branch prediction schemes always make the same prediction for a given branch, regardless of execution history.

**Predict taken**: Always predict the branch is taken. Loop branches are often taken, so this alone achieves roughly 70% accuracy, improving average CPI from 4.8 (no prediction) to about 2.14 cycles.

**Backwards Taken, Forwards Not Taken (BTFNT)**: Loop branches go backwards (to the top of the loop) and are usually taken. Forward branches (skipping ahead) are less often taken. By predicting "taken" for backwards and "not taken" for forwards, accuracy improves to about 80%, giving ~1.76 CPI. The compiler can help by arranging code so the not-taken path of a forward branch is the more likely one.

The PPC 601 (1993) and PPC 603 used the BTFNT scheme. Static schemes are simple but limited because they cannot adapt to runtime behavior.

## Prerequisites

- [[branch-prediction]] — Static prediction is the simplest category of branch prediction schemes
- [[pipelining]] — Branch prediction exists to keep the pipeline full at branches

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[branch-prediction]]
- [[dynamic-branch-prediction]]
- [[branch-prediction-performance-model]]
