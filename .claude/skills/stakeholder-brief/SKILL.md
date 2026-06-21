# Skill: Stakeholder Brief

## Trigger
Activate when the user says "write a stakeholder brief," "draft an executive update," "write a status update for [person]," "prepare a brief for [meeting]," or "how do I communicate [situation] to [stakeholder]."

---

## Behavior

### Step 1 — Understand the audience and context
Ask:
1. Who is the recipient? (Name and role — check `GOALS.md → Key Stakeholders` for existing context)
2. What's the format? (Written async / presented in a meeting / Slack message)
3. What's the main thing this person needs to know or decide?
4. What's the ask? (Approval / Awareness / Feedback / Unblock something)
5. Are there any sensitive dynamics I should be aware of? (Disagreement, prior concern, political context)

---

### Step 2 — Adapt to the recipient's profile

Before writing, check `GOALS.md → Key Stakeholders` for notes on this person. Adapt accordingly:

| If they are... | Adjust by... |
|----------------|-------------|
| An executive / C-suite | Lead with the business impact, not the feature. One paragraph max before the key ask. |
| A technical leader | Include specific tradeoffs, constraints, and open technical questions. |
| A business partner (Sales, CS, Marketing) | Frame around customer / revenue impact. Avoid internal jargon. |
| A cross-functional peer | Be direct about what you need from them and by when. |
| Your manager | Be transparent about risks and what you're uncertain about — they can't help if they don't know. |

---

### Step 3 — Write the brief

**For async briefs (doc / email):**

Use this structure — keep it under one page unless the situation demands more:

> **Subject / Title:** [Specific and informative — not "Update" or "FYI"]
>
> **TL;DR:** [One paragraph. The most important thing they need to know. Lead with the most critical, not the most recent.]
>
> **Status:** [On track / At risk / Blocked — and why in one sentence]
>
> **What's happened:** [Key facts, briefly. Bullet points if multiple items.]
>
> **What I need from you:** [Specific ask — one or two items max, with deadlines]
>
> **What happens if we don't act:** [Optional — include only if urgency matters]
>
> **Next steps:** [What you're doing next, so they're not wondering]

**For meeting presentations:**

Structure as: Context → Situation → Complication → Resolution → Ask

1. **Context** (30 sec): Here's where we are
2. **Situation** (1 min): Here's what's changed or what we're facing
3. **Complication** (30 sec): Here's the challenge or decision required
4. **Options** (2 min): Here are the paths forward with tradeoffs
5. **Resolution** (30 sec): Here's what I recommend and why
6. **Ask** (30 sec): Here's specifically what I need from you today

---

### Step 4 — Review before delivering

Check:
- [ ] The ask is specific — not "any thoughts?" but "I need a go/no-go decision by [date]"
- [ ] The TL;DR would work even if they read nothing else
- [ ] The tone matches the relationship and format
- [ ] No jargon the recipient might not know
- [ ] No banned words (leverage, synergy, robust, etc.)
- [ ] Risks are visible, not buried
- [ ] The "what I need from you" section has a deadline

---

## Difficult Stakeholder Situations

**When delivering bad news:**
- Lead with the fact, not the setup. "We're going to miss the Q2 deadline" — not three paragraphs of context first.
- Follow with the cause, what you're doing about it, and what you need.
- Offer options, not just the problem.

**When disagreeing with a stakeholder:**
- Acknowledge their position before stating yours: "I understand the priority on X — my concern is that..."
- Lead with shared goals, then the specific disagreement.
- Propose a decision-making process if you can't resolve it directly.

**When you don't have answers:**
- Say so directly: "I don't have the data on this yet. I'll have it by [date]."
- Never guess and present it as fact.
