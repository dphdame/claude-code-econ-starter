---
name: validate-estimator
description: Run the planted-truth verification routine on estimator code before trusting its results. Use when the user says "validate the estimator", "verify this implementation", "check the estimator code", or after generating any econometric estimator implementation.
---

# Validate Estimator

An estimator implementation can import cleanly, run without error, and return a coefficient in a plausible range while estimating the wrong thing. A clean run shows only that the code executed, never that the implementation matches the estimator the design requires. This skill checks the match by planting a known truth and requiring the code to recover it.

Why this routine: https://tooearlytosay.com/research/methodology/validate-ai-econometric-code/

## Prerequisites

- The estimator implementation exists as runnable code
- The source definition is available: the paper, or the canonical package documentation

## Workflow

1. **Write down the estimand** from the source before reading the generated code: which exact quantity is estimated, and how it is aggregated.
2. **Name the low-visibility choices**, where reimplementation mistakes concentrate:
   - the comparison set: which units count as controls in each comparison
   - the weighting: how cell-level effects combine into the reported estimate or path
   - the transformation window: which periods are used to remove levels, trends, or seasonality
   - the indexing: how event time aligns to each unit's treatment date
3. **Build a controlled data-generating process** and plant a true value for the target parameter (scaffolding below). Planting the truth makes the result a direct check instead of a judgment about whether a coefficient looks plausible.
4. **Run the implementation across many draws** (500 to 2,000) and require the mean estimate to recover the planted value within a stated tolerance.
5. **Break the easy symmetries** in the simulated data: unequal cohort or group sizes, unbalanced timing, missing cells. On symmetric data a weighted mean and a plain mean coincide, so a dropped weight passes the check exactly.
6. **Read the implementation line by line against the source** on every weight, aggregation rule, index, and any label that asserts a fact about the data. Report each divergence.
7. **Report a verdict:** which checks ran, which passed, which failed, and what each failure implies for the results.

## Simulation scaffolding

```python
import numpy as np

def verify_estimator(estimator, simulate_dgp, true_effect, tol, reps=1000, seed=0):
    """Plant a known effect, run the estimator across many draws, and check
    whether the mean recovers the truth. Catches biasing bugs; it does NOT
    validate identification, and it misses bugs that leave the estimate
    unbiased (see the limits section)."""
    draws = np.array([
        estimator(simulate_dgp(true_effect, np.random.default_rng(seed + i)))
        for i in range(reps)
    ])
    bias = draws.mean() - true_effect
    return {"mean": float(draws.mean()), "bias": float(bias), "passed": bool(abs(bias) <= tol)}
```

`simulate_dgp(true_effect, rng)` returns one simulated dataset with the effect planted; `estimator(data)` returns the point estimate. Write both for the design under test, keep the seeds fixed, and the check reruns identically anywhere.

## What this check cannot catch

- **Bugs the chosen process never exercises.** The check is only as strong as the planted DGP; a transformation that fails under diverging trends passes on data without them.
- **Bugs that leave the estimate unbiased.** An input-ordering error can reshuffle which draw is seen without moving the mean across seeds; only the line-by-line reading of item 6 exposes it.
- **Identification problems.** Recovering a planted value validates the implementation, never the research design. Whether the assumptions are credible stays a human judgment.

## Success criteria

- The planted value is recovered within tolerance on data that break the convenient symmetries
- The line-by-line reading against the source found no unexplained divergence
- The verdict names both what was checked and what remains unchecked
