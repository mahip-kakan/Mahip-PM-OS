# Registry

System reference and index for Mahip PMS.

---

## Contents

| File | Purpose |
|------|---------|
| `skill-index.md` | All skills — what they do, when to use them, trigger phrases, and chaining patterns |

---

## System Health Checks

Run these periodically to keep the system sharp:

### Monthly
- [ ] Review `GOALS.md` — are OKR statuses accurate?
- [ ] Archive completed tasks from `Tasks/active.md`
- [ ] Delete backlog items that are no longer relevant
- [ ] Check `Experiments/active.md` — any experiments that should have ended?

### Quarterly
- [ ] Update `GOALS.md` with new quarter OKRs
- [ ] Prune `CLAUDE.md` — remove rules that no longer earn their place
- [ ] Archive completed projects from `Projects/`
- [ ] Review `Knowledge/competitors/` — any entries older than 3 months that need refreshing?

### When Something Goes Wrong
- [ ] Add a rule to `CLAUDE.md` to prevent the same mistake next session
- [ ] If the rule is scoped to a specific type of work, put it in `.claude/rules/` instead

---

## Folder Purpose Quick Reference

| Folder | What goes here | What does NOT go here |
|--------|---------------|----------------------|
| `Tasks/` | Actionable items with owners and due dates | Ideas, backlog overflow, reference material |
| `Projects/` | One-off initiatives with a clear endpoint | Repeatable processes |
| `Workflows/` | Repeatable processes you run many times | One-off project work |
| `Meetings/` | Notes from any meeting | Action items (those go in Tasks/) |
| `Knowledge/` | Reference that persists across projects | Project-specific research |
| `Experiments/` | A/B tests and experiment results | Ideas that haven't been designed yet |
| `Templates/` | Blank document structures | Filled-in documents |
| `.claude/skills/` | Repeatable workflows triggered by natural language | One-off Claude prompts |
