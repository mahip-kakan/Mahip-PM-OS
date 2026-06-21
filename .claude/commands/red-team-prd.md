---
description: Red-team a PRD, roadmap, or strategy — attack load-bearing assumptions and return the cheapest test for each
argument-hint: "<PRD, roadmap, strategy, or @file path>"
---

# /red-team-prd — Attack the Plan Before Reality Does

Apply **strategy-red-team** to stress-test a plan using your product context.

**Before starting:** Read `CLAUDE.md`, `GOALS.md`, and `references/product-context.md`.

## Invocation

```
/red-team-prd @Projects/my-feature/requirements.md
/red-team-prd Prioritize AI onboarding — activation is our bottleneck
/red-team-prd the current doc
```

## Workflow

### Step 1: Accept the plan

PRD, roadmap, strategy memo, or `@file` path. If "the current doc," use the document in context.

Cross-check claims against `references/product-context.md` and `GOALS.md` OKRs.

### Step 2: Red-team

Apply **strategy-red-team**:
- Extract load-bearing claims only
- Steelman, then attack
- Rank by (impact if wrong) × (likelihood wrong) × (cheapness to test)
- Never fabricate weaknesses

### Step 3: Save output

Save to `Projects/[name]/red-team-[date].md` or append summary to `decisions/log.md` if a kill-assumption changes direction.

### Step 4: Offer next steps

- "Turn the top kill-assumption into an **experiment**?" → `experiment-designer` or `/discover`
- "Run a **pre-mortem**?" → `/pre-mortem`
- "Rewrite the riskiest PRD section?"
