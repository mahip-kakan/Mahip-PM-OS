# Workflow: Launch Prep

*Run this 2–4 weeks before any feature or product launch. Catches issues early enough to fix them.*

---

## Purpose

- Ensure every stakeholder is aligned before launch
- Surface go/no-go risks before they become last-minute fires
- Produce the artifacts every team needs (comms, runbook, rollback plan)
- Establish success criteria so you know what "it worked" means

---

## Inputs Claude Needs

- `Projects/[project-name]/brief.md` — what you're launching
- `Projects/[project-name]/requirements.md` — what's shipping
- `GOALS.md` — which OKR this launch is serving

---

## The Workflow

### Week T-4: Alignment Check

Prompt Claude:
> "Read the brief for [project]. Help me identify every stakeholder who needs to be aligned before we launch, what they need to know, and any gaps I should fill before going further."

Do a quick alignment check with each stakeholder. Any "I didn't know about this" at T-1 is a failure of this step.

---

### Week T-3: Launch Checklist

Trigger the launch-checklist skill:
> "Create a launch checklist for [project]. It's targeting [user segment], shipping [date], and the key risk is [your biggest concern]."

The checklist will be calibrated to your risk level. Review it and assign owners for each item.

---

### Week T-2: Artifact Review

Make sure these exist and are accurate:
- [ ] Internal announcement drafted (Slack / email)
- [ ] External announcement drafted (if user-facing)
- [ ] Support / CS briefing prepared
- [ ] Documentation updated (if applicable)
- [ ] Analytics instrumented and tested
- [ ] Feature flag or gradual rollout plan defined

---

### Week T-1: Go / No-Go

Run this prompt:
> "Based on the launch checklist for [project] and current task status, help me run a go/no-go assessment. What's complete, what's outstanding, and what are the top 3 risks to launching on [date]?"

**Go criteria:** All Must items on the checklist are complete. No P0 bugs open. Rollback plan is documented and tested.

**No-go triggers:**
- Any Must item incomplete without a clear mitigation
- Rollback plan untested or undefined
- Key stakeholder not aligned

---

### Launch Day

- [ ] Deploy during low-traffic window (if applicable)
- [ ] Monitor dashboards for first 2 hours
- [ ] Send internal launch announcement
- [ ] Send external announcement (if applicable)
- [ ] Log launch timestamp for post-launch review

**Rollback decision owner:** [FILL IN — who has authority to call a rollback?]
**Rollback trigger:** [FILL IN — what metrics or signals trigger a rollback?]

---

### T+1 Week: Post-Launch Review

Prompt Claude:
> "It's one week since we launched [project]. Help me write a post-launch review. We were targeting [metric], here's what happened: [paste data]."

The review should cover:
- Did we hit our success metrics?
- What surprised us?
- What would we do differently?
- What follow-up work did we create?

Archive the project if the work is complete.
