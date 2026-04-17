---
tags:
  - concept
  - ece459
  - hardware
  - L06
  - L07
prerequisites:
  - "[[pipelining]]"
  - "[[pipeline-hazards]]"
  - "[[speculation]]"
---

# Branch Prediction

Branch prediction is the hardware (and sometimes compiler) mechanism for guessing the outcome of a branch instruction before it is resolved. It enables [[pipelining]] by keeping the pipeline full rather than stalling at every branch.

Branch prediction is usually right 95% or more of the time. When correct, execution proceeds without penalty. When wrong, the pipeline must be flushed (all speculatively executed work is discarded), incurring a significant penalty -- potentially 20+ cycles on modern processors.

The course covers a progression of branch prediction schemes, from simple static approaches to sophisticated dynamic ones:

- **No prediction**: Serialize at every branch. Very slow.
- [[static-branch-prediction]]: Predict always taken, or use BTFNT (backwards taken, forwards not taken).
- [[dynamic-branch-prediction]]: Use per-branch execution history. Includes 1-bit schemes, [[two-bit-saturating-counter]], [[two-level-adaptive-predictor]], and [[gshare-predictor]].

The compiler and CPU's branch prediction routines are very good -- trying to outsmart them with [[likely-unlikely-hints]] is usually not beneficial. See [[branch-prediction-performance-model]] for quantitative analysis.

## Prerequisites

- [[pipelining]] — Branch prediction exists to keep the pipeline full at branch points
- [[pipeline-hazards]] — Branches cause control hazards that prediction mitigates
- [[speculation]] — Branch prediction drives speculative execution of the predicted path

## Lectures

- [[L06-Modern-Processors]]
- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[pipelining]]
- [[speculation]]
- [[pipeline-hazards]]
- [[static-branch-prediction]]
- [[dynamic-branch-prediction]]
- [[branch-prediction-performance-model]]
- [[spectre-and-meltdown]]
