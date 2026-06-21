# Skill: PRD Writer

## Trigger
Activate when the user asks to "write a PRD," "create a PRD," "draft a product requirements doc," or "spec out [feature]."

---

## Behavior

### Step 1 — Clarify before generating
Ask exactly these questions before writing a single word of the PRD. Do not skip this step.

1. What stage is this PRD for? (Team Kickoff / Planning Review / XFN Kickoff / Solution Review / Launch Readiness / Impact Review)
2. Who is the primary user experiencing this problem, and what's the clearest evidence this problem is real?
3. What does success look like in 90 days — one specific metric with a target number?
4. What's explicitly out of scope that stakeholders might assume is included?
5. Are there known engineering or data constraints I should design around?

Wait for answers. If the user says "just draft something," acknowledge the gaps you're making assumptions about and proceed.

---

### Step 2 — Determine output depth by stage

| Stage | Length | Key sections |
|-------|--------|--------------|
| Team Kickoff | 1 page | Problem, hypothesis, proposed solution, open questions |
| Planning Review | 1–2 pages | + Success metrics, non-goals, constraints |
| XFN Kickoff | 2 pages | + Dependencies, launch plan, risks |
| Solution Review | 2 pages | + Full requirements, edge cases, rollback plan |
| Launch Readiness | 1 page | Metrics, go/no-go criteria, rollback |
| Impact Review | 1 page | Results vs. targets, learnings |

Default to the shortest appropriate length. Ask before exceeding 2 pages.

---

### Step 3 — Write the PRD

Use the structure from `Templates/prd-template.md`. Always include:
- A testable hypothesis (not a feature description)
- Evidence the problem is real (not assumed)
- Specific metrics with baselines and targets — never directional ("increase engagement")
- Explicit non-goals
- Risks with mitigations, not just a risk list
- `[NEED: data from X]` for every gap — never invent numbers or quotes

---

### Step 4 — Self-review before delivering

Check every section against these criteria:
- [ ] Hypothesis is falsifiable — someone could prove it wrong
- [ ] Problem has evidence, not just intuition
- [ ] Metrics are specific (number + timeframe + measurement method)
- [ ] Non-goals are explicit, not assumed
- [ ] Risks have mitigations, not just descriptions
- [ ] No fabricated data, quotes, or competitor claims
- [ ] AI-specific sections filled in if this is an AI feature (model type, evals, failure modes)

---

## Anti-Patterns (Common PRD Mistakes to Avoid)

- **Solutioning the problem statement.** The problem section should describe user pain, not the product fix.
- **Vague success metrics.** "Improve retention" is not a metric. "Increase 30-day retention from 41% to 50% by [date]" is.
- **Missing non-goals.** Without explicit non-goals, every stakeholder reads in what they hoped for.
- **Risks without mitigations.** A risk list is just a worry list. Pair every risk with a specific mitigation.
- **Fabricated data.** If you don't have the number, write `[NEED: data from analytics team]`. Never guess and present it as fact.
- **AI features without failure mode documentation.** Always define what bad output looks like and how users recover.

---

## Example: Good vs. Bad Hypothesis

**Bad:** "We'll add an AI summarization feature to help users."
**Good:** "We believe that adding AI-generated summaries to search results will reduce time-to-first-action from 45s to under 20s for users who search 3+ times per session, measured by median time from search to first click."
