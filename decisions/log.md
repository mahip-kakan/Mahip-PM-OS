# Decisions Log

Append-only record of significant PM decisions, trade-offs, and rationale. Never delete entries — add a follow-up note if a decision was reversed.

*Claude should suggest logging a decision here whenever a significant trade-off is made. Trigger: "Log this decision."*

---

## Format

```
## [YYYY-MM-DD] — [Decision title]

**Context:** What situation or question prompted this decision?
**Decision:** What was decided?
**Rationale:** Why this option over alternatives?
**Trade-offs:** What did we give up? What risk did we accept?
**Revisit if:** Under what conditions should this be reconsidered?
```

---

## Log

*(Entries appear below this line, newest first.)*

---

## [YYYY-MM-DD] — PM-OS initialized

**Context:** Cloned Mahip-PM-OS and ran `/onboard` to set up the system.
**Decision:** Adopted this PM-OS structure as the primary AI operating environment.
**Rationale:** Need persistent context, structured PM skills, and a self-improving workflow system that works inside Claude Code.
**Trade-offs:** Time investment to fill in context files upfront.
**Revisit if:** A significantly better PM-OS architecture emerges, or if Claude Code's native features make this redundant.
