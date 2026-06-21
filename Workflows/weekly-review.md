# Workflow: Weekly Review

*Run this every Friday (or Monday morning). It takes 20–30 minutes and keeps you from losing track of what matters.*

---

## Purpose

- Reflect on what shipped, what didn't, and why
- Update task and project status so Monday starts with clarity
- Groom the backlog so nothing important is buried
- Identify the 1–3 most important things for next week
- Draft a stakeholder update if one is due

---

## Inputs Claude Needs

Before running this workflow, make sure these are current:
- `Tasks/active.md` — today's state, not last week's
- `GOALS.md` — OKRs for the quarter
- Any meeting notes from this week (in `Meetings/`)

---

## The Workflow

### Step 1 — Reflect on Last Week

Prompt Claude:
> "Read my active tasks and summarize what I shipped, what's still in progress, and what got blocked this week."

Then answer these questions (Claude will prompt you):
- What was the most important thing I did this week?
- What didn't happen that should have?
- What surprised me?
- What should I have delegated?

---

### Step 2 — Update Task Status

Go through `Tasks/active.md` and update every task status. Move completed tasks to `Tasks/archive/[YYYY-MM]/`. Move stalled tasks back to backlog with a note on why.

Prompt Claude:
> "Help me clean up my active tasks list. I'll tell you what's done, what's blocked, and what needs to move."

---

### Step 3 — Check OKR Progress

Prompt Claude:
> "Read my GOALS.md and tell me how my active tasks map to my quarterly OKRs. What am I making progress on? What OKR has had no movement this week?"

Update `GOALS.md` with current status if anything changed.

---

### Step 4 — Groom the Backlog

Open `Tasks/backlog.md`. For each item:
- Does it still matter? If not, delete it.
- Is it now higher priority than something in active? Swap them.
- Can it be broken into a smaller next action?

Target: backlog should be under 20 items. If it's longer, your definition of "backlog" is too loose.

---

### Step 5 — Set Next Week's Priorities

Prompt Claude:
> "Based on my OKRs and current task state, what are the 3 most important things I should focus on next week? What should I say no to?"

Write the 3 priorities at the top of `Tasks/active.md` for next week.

---

### Step 6 — Draft Stakeholder Update (If Due)

If you owe your manager or team a weekly update, trigger the stakeholder-brief skill:
> "Write a weekly stakeholder update for [manager name]. We shipped [X], [Y] is in progress, [Z] is at risk. The ask is [what you need from them]."

---

### Step 7 — Automation Discovery (Friday only, ~10 min)

*Run this step on Fridays. Skip on Monday reviews.*

Ask yourself: **what did I do 3+ times this week that felt manual or repetitive?**

Common PM candidates:
- Writing the same type of stakeholder update repeatedly
- Formatting data from one tool into a doc for another
- Looking up the same competitor / metric baseline every time you spec a feature
- Running the same research synthesis process on new interview batches
- Copy-pasting meeting notes into a structured template

Prompt Claude:
> "Based on my tasks this week and my GOALS.md, what's the highest-leverage PM workflow I'm doing manually that you could help automate or speed up?"

If something surfaces: run `/level-up` to scope and ship it. Don't try to scope it inside the weekly review — keep them separate.

If nothing surfaces: that's fine. Note it and move on.

---

## Output

By the end of this workflow you should have:
- [ ] Updated `Tasks/active.md` with accurate statuses
- [ ] Archived completed tasks
- [ ] Updated OKR progress in `GOALS.md`
- [ ] A clean backlog (under 20 items)
- [ ] 3 clear priorities written at the top of active tasks
- [ ] Stakeholder update drafted (if applicable)
- [ ] (Friday only) One automation candidate identified — or explicitly noted that none surfaced
