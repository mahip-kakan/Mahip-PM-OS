---
description: Analyze A/B test results — significance, sample size check, ship/extend/stop recommendation
argument-hint: "<test results, CSV, or @Experiments/active.md>"
---

# /analyze-test — A/B Test Analysis

Apply **ab-test-analysis** to experiment results. Pairs with `experiment-designer` (design) → this command (interpret).

**Before starting:** Read `Experiments/active.md` and `GOALS.md` for pre-registered hypotheses and decision criteria.

## Invocation

```
/analyze-test Control: 4.2% (n=5000), Variant: 4.8% (n=5100)
/analyze-test @Experiments/active.md
/analyze-test [upload CSV]
```

## Workflow

### Step 1: Accept data

Summary stats, CSV, screenshot, or reference to `Experiments/active.md`.

### Step 2: Validate test design

Check sample size, duration, randomization, external factors. Flag flawed tests before interpreting.

### Step 3: Analyze

Apply **ab-test-analysis** — p-value, CI, practical significance, segment breakdown if available.

If `connections.md` lists an analytics DB MCP, offer to pull fresh data via **sql-queries**.

### Step 4: Save and update

Update `Experiments/active.md` with results and **SHIP / EXTEND / STOP** recommendation.

Log decision to `decisions/log.md`.

### Step 5: Offer next steps

- "Design a **follow-up experiment**?" → `experiment-designer`
- "Draft a **stakeholder update** on results?" → `stakeholder-brief`
- "Generate **monitoring SQL**?" → `sql-queries`
