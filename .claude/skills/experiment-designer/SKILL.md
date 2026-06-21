# Skill: Experiment Designer

## Trigger
Activate when the user says "design an experiment for," "help me set up an A/B test," "what should I test," "how do I test [hypothesis]," or "experiment design for [feature]."

---

## Behavior

### Step 1 — Clarify the hypothesis and context
Ask:
1. What behavior or outcome are you trying to change?
2. What's the specific change you want to test? (The treatment — be precise)
3. Who is the target user segment?
4. What's the primary metric you'll use to judge success?
5. What's the current baseline for that metric?
6. How much traffic hits this surface per week?

Do not proceed until you have at least a rough answer to each question.

---

### Step 2 — Validate the hypothesis

The hypothesis must be:
- **Falsifiable:** A specific result that could prove it wrong
- **Causal:** We believe X *causes* Y — not just that X and Y are correlated
- **Measurable:** The outcome can be tracked with available instrumentation

Help the user rewrite vague hypotheses into testable ones:

> **Vague:** "We think users will like the new design"
> **Testable:** "We believe changing the CTA from 'Learn more' to 'Start free' will increase click-through rate from 12% to 17% for users on the pricing page, because it reduces ambiguity about the next step."

---

### Step 3 — Design the experiment

#### Experiment Design Document

**Name:** [Short, descriptive — includes the variable being tested]

**Hypothesis:** We believe that **[treatment change]** will **[expected effect]** for **[user segment]**, because **[reasoning]**.

**Variants:**
- **Control (A):** [Exact description of current experience]
- **Treatment (B):** [Exact description of the change being tested]
- **Treatment (C):** [Only if testing multiple variants — describe precisely]

**Primary metric:**
| Metric | Definition | Baseline | Target lift | Measurement method |
|--------|------------|----------|-------------|-------------------|
| [Name] | [Exact definition] | [Value] | [e.g., +5% relative] | [Event / query] |

**Secondary metrics:** [2–3 supporting signals to watch]
**Guardrail metrics:** [What must not regress — with acceptable floors]

---

#### Statistical Design

| Parameter | Value | Source |
|-----------|-------|--------|
| Minimum detectable effect (MDE) | [% relative lift] | [Business rationale for why smaller lifts don't matter] |
| Statistical power | 80% (standard) | |
| Significance threshold | p < 0.05 (95% confidence) | |
| Required sample size per variant | [Calculated — see below] | Sample size calculator |
| Weekly traffic to surface | [From user input] | |
| Estimated experiment duration | [Required sample ÷ weekly traffic] | |

**Sample size guidance:**
- MDE 10%+: Usually achievable in 1–2 weeks
- MDE 5%: Often requires 3–6 weeks
- MDE <5%: May not be practical — reconsider whether this experiment is worth running

*If experiment duration exceeds 8 weeks, reconsider the design. Long experiments are vulnerable to novelty effects, seasonal shifts, and focus drift.*

---

#### Audience and Segmentation
- **Eligible users:** [Definition — who qualifies for the experiment]
- **Traffic split:** [e.g., 50/50 — or justify if uneven]
- **Exclusions:** [Who to exclude and why — prior experiment participants, internal users, etc.]
- **Stratification:** [Any subgroups to ensure equal distribution across — e.g., device type, user tenure]

---

#### Decision Framework

*Define this BEFORE running the experiment. Never decide criteria after seeing results.*

| Outcome | Decision |
|---------|----------|
| Primary metric improves ≥ MDE, no guardrail regressions | Ship treatment |
| Primary metric improves < MDE at end of duration | Do not ship — insufficient evidence |
| Any guardrail metric regresses beyond acceptable floor | Stop experiment, investigate |
| Significant positive in a secondary metric only | Consider a follow-up experiment, not a ship decision |
| Inconclusive at full duration | Document learnings, do not ship on ambiguous evidence |

**Decision owner:** [Name]
**Decision deadline:** [Date]

---

#### Risks and Mitigations

| Risk | Mitigation |
|------|------------|
| Novelty effect inflating early results | Run full duration; don't call early winners |
| Instrumentation gap — metric not tracked | Verify before starting |
| Sample size too small to detect effect | Extend duration or increase scope |
| Multiple tests running simultaneously | Check for experiment collision — conflicting treatment arms |

---

### Step 4 — Create the experiment file

Save the design to:
`Experiments/[experiment-name].md`

Update `Experiments/active.md` with a summary row.

---

## Anti-Patterns

- **Peeking at results.** Looking at p-values before the experiment completes and stopping early when it looks good is p-hacking. Run the full planned duration.
- **No pre-registered decision criteria.** If you decide what "win" means after seeing the data, you can rationalize any result.
- **Too many variants.** Each additional variant requires more sample size and introduces more complexity. Two variants is usually enough.
- **Testing too many changes at once.** If you change 5 things simultaneously, you can't know which caused the result. Test one thing.
- **Ignoring guardrail metrics.** A 10% lift in signups doesn't matter if it came with a 15% drop in week-2 retention.
- **Calling a neutral result a failure.** A well-designed null result is valuable information. It tells you the hypothesis was wrong — that's worth knowing.
