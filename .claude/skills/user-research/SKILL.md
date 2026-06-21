# Skill: User Research Synthesizer

## Trigger
Activate when the user says "synthesize this research," "analyze these interview notes," "what patterns are in these notes," or "turn these notes into insights."

---

## Behavior

### Step 1 — Understand the inputs
Ask:
1. What type of research is this? (User interviews, survey responses, support tickets, session recordings, usability test notes)
2. How many participants / data points?
3. What was the research question or goal?
4. What decision will these findings inform?

Then ask the user to paste or link to the raw notes.

---

### Step 2 — Synthesize

Organize findings into this structure:

#### Research Summary
- **Method:** [Interview / Survey / Usability test / etc.]
- **Participants:** [N = X; brief description of who they are]
- **Research goal:** [One sentence]
- **Date(s) conducted:** [If known]

---

#### Top Findings (Ranked by Evidence Strength)

For each finding:

**Finding [N]: [Short, direct title — a complete sentence, not a label]**

*Evidence strength: Strong (5+ participants) / Moderate (3–4) / Weak (1–2) / Single data point*

> "[Direct quote — most illustrative example]"
> — [Participant descriptor, e.g., "Power user, 3 years on platform"]

**What the data shows:** [Summary of what multiple participants said or did]
**Frequency:** [Seen in X of Y participants]
**Implication:** [What does this mean for what we should build or change?]

---

#### Patterns and Tensions

**Patterns** — Things that came up across multiple participants in consistent ways:
- [Pattern + evidence count]

**Tensions** — Contradictions in what users said vs. what they did, or between user groups:
- [Tension + explanation]

**Surprises** — Things you didn't expect to find:
- [Surprise + what it changes about your thinking]

---

#### Open Questions

What the research raised but didn't answer — worth following up on:
- [ ] [Question — suggested follow-up method]
- [ ] [Question]

---

#### Recommended Next Steps

Based on the research, what should happen next?

| Action | Priority | Who |
|--------|----------|-----|
| [Action] | High / Med | [Team or person] |
| [Action] | High / Med | [Team or person] |

---

## Important Rules

- Always distinguish between what users **said** and what users **did** — behavior beats stated preference.
- Never generalize from 1–2 participants as if it's a universal truth. Mark weak evidence clearly.
- Flag when findings conflict with existing product assumptions — that's often the most valuable output.
- Do not add findings that aren't in the source material. If something wasn't asked or observed, don't infer it.
- Save the synthesis to `Knowledge/users/[research-topic]-[date].md` for future reference.
