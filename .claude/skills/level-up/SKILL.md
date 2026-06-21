---
name: level-up
description: Weekly PM automation discovery. Surfaces one workflow you're doing manually that Claude could do faster or better. Trigger on "level up", "what should I automate", "find me leverage this week", "what's repeatable in my work", or as a Friday ritual. One run = one scoped automation candidate + one artifact.
---

## What this skill does

Runs a structured 3-phase interview every week (or on-demand) to surface one PM workflow worth automating, scope it correctly, and ship one artifact — a new skill, a saved prompt template, or a workflow playbook.

**The compounding effect:** after 4–6 runs, you start spotting automation candidates mid-week without being asked. The questions become internal defaults. That's the goal.

---

## What `/level-up` is NOT

- Not `/health-audit`. That's structural ("is the PM-OS built right?"). This is functional ("what PM work am I doing manually that I shouldn't be?").
- Not a multi-candidate planner. One run = one scoped artifact.
- Not a capability planner. It doesn't suggest skills you should install — it surfaces workflows *you* are doing that a skill could replace.

---

## When to run

- **First run: after `/onboard` is complete and you've used the system for at least one week.** Earlier yields nothing concrete — no usage patterns to surface.
- **Cadence: Friday afternoon.** Review the week, surface one candidate, ship Monday.
- **On-demand any time** a manual task feels repetitive mid-week.

---

## Inputs the skill reads

- `GOALS.md` — priorities and OKRs (what work should be getting done)
- `Tasks/active.md` and `Tasks/backlog.md` — recent work patterns
- `connections.md` — what tools are reachable
- `decisions/log.md` — recent decisions (what's already been built or considered)
- `.claude/skills/*/SKILL.md` frontmatter — what capabilities already exist
- `Workflows/weekly-review.md` — to avoid duplicating what's already a workflow

---

## Execution — three phases

### Phase 1 — Find the candidate (Mindset interview)

Surface 1–3 PM workflow candidates ranked by leverage. Ask these conversationally, one at a time:

1. *"Walk me through your week. What PM task did you do 3+ times?"* (frequency signal)
2. *"Anything that felt like copy-paste work — same inputs, same output every time?"* (deterministic signal)
3. *"Anything you did where you thought 'I could explain this to a junior PM in 5 minutes'?"* (delegation signal)
4. *"What took the most calendar time vs. the least strategic value?"* (leverage signal)
5. *"If your workload doubled tomorrow, what would break first?"* (constraint signal)

After the user answers, surface 1–3 candidates. For each, name:
- What the task is
- How often it recurs
- Which of your quarterly OKRs it touches (or doesn't — "no OKR connection" is worth noting)
- One-line "why this is leverage"

Ask: *"Which one should we scope?"*

---

### Phase 2 — Scope it correctly (Method)

User picks one candidate. Walk through 5 scoping steps:

**Step 1 — Check the OKR connection.**
*"Which of your quarterly OKRs does automating this move? If none, are you sure this is the right thing to build?"*

If there's no OKR connection, flag it. Don't block — the user may have a valid reason (e.g., it's overhead that's preventing OKR work). But make them name the reason. Log it.

**Step 2 — Eliminate first.**
*"What happens if we just stop doing this task entirely?"*

- If the answer is "nothing important breaks" → skill exits cheerfully. That's a win. Log to `decisions/log.md`: "Decided to eliminate [task] — it was overhead with no real output."
- If stopping would break something → proceed to Step 3.

**Step 3 — Map the process.**
The user must be able to describe the task as five elements:
- **Trigger:** what kicks it off
- **Inputs:** what data or context is needed
- **Steps:** what transformations happen
- **Decision points:** where it branches based on context
- **Output:** what gets produced and where it goes

If the user can't describe all five: *"If you can't explain this to a person in 5 steps, you can't spec it as a skill. Sketch it first — we can scope it next session."* Stop.

**Step 4 — Pick the automation level.**

| Level | Name | What it means |
|-------|------|---------------|
| L0 | Manual | No AI. User does everything. |
| L1 | Prompted | Claude assists when explicitly asked. No skill needed. |
| L2 | Templated | Saved prompt template. User runs it, Claude executes. |
| L3 | Skilled | A SKILL.md that runs when triggered by natural language. |
| L4 | Chained | A sequence of skills that hand off automatically. |

**Default = lowest level that meaningfully reduces friction.** Push back on L4 unless L3 has been running cleanly for 2+ weeks. Most first-time automations should be L2 or L3.

*"Workflows beat agents. If a decision doesn't HAVE to be made by Claude, don't delegate it to Claude."*

**Step 5 — Tie to a metric.**
*"What changes when this runs well? Name a specific number."* Examples: "saves 45 min/week", "reduces PRD review cycles from 3 to 1", "stakeholder update drafted in 10 min instead of 60".

If the user can't name a concrete improvement: *"If this automation doesn't save time or improve quality on something measurable, what's the case for building it?"* Don't block — but make them articulate the value before shipping.

Log the scope to `decisions/log.md`:
```
## [date] — Level-up: [task name]
**Candidate:** [what the task is]
**OKR connection:** [which OKR or "none — rationale"]
**Automation level:** L[X] — [name]
**Process map:** Trigger: [X] | Inputs: [X] | Steps: [X] | Decision points: [X] | Output: [X]
**Expected improvement:** [metric or time saving]
```

---

### Phase 3 — Ship one artifact (Machine)

Ask: *"How do you want to ship this?"* Present options in order:

1. **Saved prompt template** — a prompt in `Templates/` the user runs manually. Zero infrastructure. Best for L1/L2.
2. **Workflow playbook** — a step-by-step Markdown file in `Workflows/` with Claude prompts embedded. Best for multi-step processes that run on a schedule.
3. **New skill** — a `SKILL.md` in `.claude/skills/[name]/`. Best for L3 — repeatable tasks triggered by natural language. Most common output.
4. **Skill chain** — updates `_Registry/skill-index.md` with a new chaining pattern. Best for L4 when two existing skills should sequence automatically.

Default = option that matches the automation level chosen in Phase 2.

**Once chosen, build the artifact inline.** For a new skill, write a complete `SKILL.md` with:
```yaml
---
name: [skill-name]
description: [one sentence — what it does and when to trigger it]
---
```
Then behavior steps, anti-patterns, and any `[NEED: data from X]` gaps flagged explicitly.

After building: ask the user to register the skill in `_Registry/skill-index.md`.

---

### Closing screen

Print after the artifact ships:

```
✓ Level-up complete.

Scoped:  [task name] → [automation level]
Built:   [artifact type] at [path]
Impact:  [expected improvement]

Run it manually 3 times before trusting it fully.
Next /level-up: Friday.
```

---

## Critical implementation rules

1. **One run = one artifact.** No parallel scoping of multiple candidates.
2. **Mindset phase always runs first.** Even if the user comes in with a pre-formed idea — run the 5 questions to validate it's the highest-leverage candidate.
3. **Eliminate-first is mandatory.** If the task can be eliminated, that's the win. Exit cheerfully.
4. **Default to the lowest autonomy level.** L3 is not always better than L2.
5. **OKR connection must be named.** Not blocked, but named.
6. **Metric must be named.** Not blocked, but named.
7. **Every artifact ships with the automation level in frontmatter.** Add `automation-level: L[X]` to the YAML frontmatter of any new SKILL.md.
8. **Read-only on existing files except `decisions/log.md` and the new artifact.**

---

## Verification

- **No usage patterns yet:** user runs `/level-up` on Day 1. Expected: skill explains it needs a week of usage first, offers to do a hypothetical scan of `GOALS.md` instead.
- **Eliminate-first test:** user names a task that's pure overhead. Expected: skill suggests elimination, exits, logs the win.
- **L4 push-back:** user asks for a fully autonomous skill on first build. Expected: skill recommends L2 or L3 first.
- **No metric named:** user can't articulate improvement. Expected: skill flags this but doesn't block — asks once, accepts the answer, notes it in the log entry.
