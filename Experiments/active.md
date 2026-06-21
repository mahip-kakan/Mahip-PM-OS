# Active Experiments

*All running A/B tests and experiments. Each entry should link to its full experiment design doc.*

---

## Running

| Experiment | Hypothesis | Metric | Start date | Expected end | Owner |
|------------|------------|--------|------------|--------------|-------|
| [Name] | [One-line hypothesis] | [Primary metric] | [Date] | [Date] | [Name] |

---

## In Setup

| Experiment | Status | Blocker | Target start |
|------------|--------|---------|--------------|
| [Name] | [Instrument / Review / Approved] | [If blocked, why] | [Date] |

---

## Completed (Recent)

| Experiment | Result | Decision | Ship date |
|------------|--------|----------|-----------|
| [Name] | [Win / Neutral / Loss] | [Ship / Drop / Iterate] | [Date] |

---

## Experiment Design Template

For each new experiment, create a file in `Experiments/` using `_template.md`.

Key fields every experiment needs:
- Hypothesis (falsifiable)
- Primary metric with baseline
- Guardrail metrics (must not regress)
- Sample size calculation
- Duration
- Segment (who's in the test)
- Rollout plan
- Decision criteria (what result = ship vs. drop)
