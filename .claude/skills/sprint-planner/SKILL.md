# Skill: Sprint Planner

## Trigger
Activate when the user says "plan this sprint," "help me plan sprint [number]," "what should go in the sprint," or "sprint planning for [date range]."

---

## Behavior

### Step 1 — Gather inputs
Ask for:
1. Team composition and capacity (people × days available this sprint)
2. Current backlog with rough estimates (points or t-shirts)
3. Sprint duration (default: 2 weeks)
4. The proposed sprint goal (1 sentence)
5. Any known dependencies, blockers, or time-offs

---

### Step 2 — Calculate usable capacity

**Rule:** Plan to 80% of theoretical capacity. Above 80% = >50% chance of missing the sprint goal.

```
Theoretical capacity = team members × sprint days × avg points per person per day
Usable capacity      = theoretical capacity × 0.80
```

Show the calculation transparently. Explain why you're using 80%, not 100%.

---

### Step 3 — Build the sprint plan

**Priority order for slot selection:**
1. Must-do items (committed to stakeholders or blocking another team)
2. Sprint goal items
3. Bug fixes affecting the sprint goal
4. Stretch items (explicitly labelled as such)

**Dependency check:** Flag every item that can't start without something external. Items with unresolved external dependencies cannot enter the sprint without a mitigation plan.

**Output format:**

| Item | Points | Priority | Owner | Dependency / Risk |
|------|--------|----------|-------|------------------|
| [Story name] | [X] | Must | [Name] | None |
| [Story name] | [X] | Goal | [Name] | Blocked by: [Team] — mitigated by [action] |
| [Story name] | [X] | Stretch | [Name] | None |

**Total committed:** [X] points (≤ usable capacity)
**Stretch:** [X] additional points if team finishes early

---

### Step 4 — Surface risks

Flag the top 3 risks to achieving the sprint goal, with specific mitigations:

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk] | High/Med | High/Med | [Specific action] |

---

### Step 5 — Write the sprint goal

If the user hasn't provided one, draft a sprint goal based on the committed items:

> "By end of sprint, [user-facing outcome] so that [business or user value]."

The sprint goal should be achievable with the committed items, but not merely a list of those items.

---

## Anti-Patterns

- **Planning to 100% capacity.** Interruptions, bug fixes, and review cycles always consume unplanned time.
- **No sprint goal.** A sprint without a goal is just a list of tasks. Teams don't rally around task lists.
- **Unresolved dependencies entering the sprint.** If the dependency isn't resolved before sprint start, the item will be blocked mid-sprint.
- **Stretch items presented as committed.** Label them explicitly. Stakeholders should not count on stretch items.
