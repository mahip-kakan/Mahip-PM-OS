---
description: Run a full product discovery cycle — assumption mapping, prioritization, and experiment design
argument-hint: "<product or feature idea>"
---

# /discover — Full Discovery Cycle

Structured discovery for Mahip PM-OS. Chains discovery skills with your persistent context.

**Before starting:** Read `CLAUDE.md`, `GOALS.md`, and `references/product-context.md` (if it exists).

## Invocation

```
/discover Smart notification system for our project management tool
/discover AI writing assistant for non-native speakers
/discover
```

## Workflow

### Step 1: Load context

Read:
- `GOALS.md` — quarterly OKRs and priorities
- `references/product-context.md` — existing PRDs, product briefs, terminology
- `Knowledge/users/` — any prior research
- `Projects/` — related active initiatives

Ask if missing:
- What are you exploring? (idea, feature area, opportunity)
- Existing product or new product?
- What decisions will this inform? (build/kill, prioritize, pivot)
- What do you already know? (research, feedback, data)

### Step 2: Divergent ideas (if needed)

If the user has a clear feature idea, skip to Step 3.

Otherwise, brainstorm 5–10 ideas from PM, Designer, and Engineer perspectives. Present with brief rationale. Ask user to pick 1–3 to stress-test.

**Checkpoint:** "Which ideas should we validate? Pick 1–3."

### Step 3: Identify assumptions

Apply **identify-assumptions-existing** (existing product) or ask user to confirm new-product context.

Surface assumptions across Value, Usability, Feasibility, Viability (and Go-to-Market for new products).

### Step 4: Prioritize assumptions

Apply **prioritize-assumptions** — Impact × Risk matrix, leap-of-faith assumptions ranked.

**Checkpoint:** "Here are your riskiest assumptions. Which should we test first?"

### Step 5: Design experiments

Apply **brainstorm-experiments-existing** (or new-product variant if applicable).

Design 1–2 experiments per critical assumption with success criteria, timeline, and effort.

### Step 6: Save discovery plan

Save to `Projects/[slug]/discovery-plan.md` or `Knowledge/discovery-[topic]-[date].md`:

```markdown
## Discovery Plan: [Topic]
**Date:** [today]
**Product stage:** existing / new
**Discovery question:** [what we're learning]

### Critical assumptions
| # | Assumption | Category | Impact | Uncertainty | Priority |

### Validation experiments
| # | Tests assumption | Method | Success criteria | Effort | Timeline |

### Decision framework
- If [experiment] succeeds → [next step]
- If [experiment] fails → [pivot/kill/investigate]
```

Log significant decisions to `decisions/log.md`.

### Step 7: Offer next steps

- "Want me to **write a PRD** for the top idea?" → `prd-writer`
- "Should I **design an interview script**?" → `interview-script`
- "Want me to **define metrics**?" → `metrics-definer`
- "Should I **red-team** the leading idea?" → `/red-team-prd`

## Notes

- 15–30 minute workflow — say this upfront
- Use `@path/to/file` for existing PRDs and research; don't ask user to re-paste what's in the repo
- For existing products, check `connections.md` for analytics MCPs before assuming no data exists
