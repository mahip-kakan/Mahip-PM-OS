# Skill: Roadmap Prioritizer

## Trigger
Activate when the user says "prioritize these features," "help me build the roadmap," "rank these opportunities," "what should we do next quarter," or "RICE scoring for [items]."

---

## Behavior

### Step 1 — Gather the candidates
Ask:
1. What's the list of features / initiatives to evaluate? (Ask the user to list them or paste a backlog)
2. What's the planning horizon? (Next sprint / quarter / half / year)
3. What are the top 1–2 OKRs this roadmap should serve? (Check `GOALS.md`)
4. Are there any non-negotiables — things that must be on the roadmap regardless of score?
5. Are there any hard constraints — things that can't be done regardless of score?

---

### Step 2 — Score with RICE

For each item, calculate a RICE score:

**RICE = (Reach × Impact × Confidence) / Effort**

| Dimension | Definition | Scale |
|-----------|------------|-------|
| **Reach** | How many users affected per quarter | Actual number estimate |
| **Impact** | How much does this move the key metric per user? | 0.25 (minimal) / 0.5 / 1 / 2 / 3 (massive) |
| **Confidence** | How confident are we in the estimates? | 50% (low) / 80% (medium) / 100% (high) |
| **Effort** | Person-weeks of work across all roles | Actual estimate |

Present in a table:

| Feature | Reach | Impact | Confidence | Effort | RICE Score |
|---------|-------|--------|------------|--------|------------|
| [Feature A] | [X users] | [1.0] | [80%] | [4 weeks] | [(X × 1.0 × 0.8) / 4] |
| [Feature B] | [X users] | [2.0] | [50%] | [8 weeks] | [...] |

*Flag every estimate that is a guess — never present uncertain numbers as facts.*

---

### Step 3 — Apply strategic fit filter

RICE score is a starting point, not the final answer. Apply a strategic fit check:

For each item, ask:
- **OKR alignment:** Does this directly move a current OKR? (High / Partial / No)
- **Strategic fit:** Does this advance a long-term strategic priority? (High / Partial / No)
- **Technical debt / platform:** Does this enable future work? (Yes / No)
- **Customer commitment:** Is this promised to a key customer or partner? (Yes / No)

Items that score low on RICE but high on OKR alignment or customer commitment should be surfaced explicitly — not automatically dropped.

---

### Step 4 — Produce a prioritized roadmap

Output three tiers:

**Tier 1 — Now (This quarter / sprint)**
[Top items by RICE score + strategic fit — these have the highest confidence and impact per effort]

| Feature | RICE | OKR | Rationale |
|---------|------|-----|-----------|
| [Feature] | [Score] | [Obj X] | [Why this makes the cut] |

**Tier 2 — Next (Following quarter)**
[Items with strong signal but not quite ready — often blocked by data, design, or a Tier 1 dependency]

**Tier 3 — Later / Evaluate**
[Items worth keeping but not prioritizing yet — revisit in 90 days]

**Explicit drops:**
[Items that scored low across all dimensions — name them and explain why, so there's no ambiguity]

---

### Step 5 — Surface trade-offs

Before finalizing, flag the top 2–3 trade-offs in the prioritization:

> "By choosing [Feature A], we're deprioritizing [Feature B]. The trade-off is [X]. Here's why I'd recommend this despite that trade-off: [reasoning]."

Stakeholders should understand what's NOT on the roadmap — and why.

---

## Anti-Patterns

- **Scoring theater.** If every item gets a high RICE score, your estimates are probably optimistic. Challenge the assumptions.
- **Ignoring qualitative signals.** RICE doesn't capture strategic bets, trust-building features, or technical foundations. These need a manual adjustment.
- **A roadmap with no deprioritizations.** A roadmap that lists everything is not a roadmap — it's a wish list. Force the hard calls.
- **Hiding the trade-offs from stakeholders.** Surface what's NOT happening. That's where the real alignment work is.
- **Effort optimism.** Teams consistently underestimate effort. Apply a 1.5–2x buffer if historical velocity data is available.
