---
name: onboard
description: Use on Day 1, when someone says "set me up", "onboard me", "let's get started", or has just cloned the repo. Runs a personalized interview (boss, competitors, stakeholders, document uploads with auto-summarize) and auto-fills all context files. Idempotent — re-run any time to refresh.
---

## What this skill does

Personalized setup wizard for Mahip PM-OS. Runs a **structured interview** (one question at a time), then a **document upload phase** where every file is automatically classified, summarized, saved to the right folder, and indexed.

**Optimized for:** Claude Cowork and Claude Code.

**Document uploads:** Every upload triggers **ingest-document** — not just chat context. Files land in `Projects/`, `Knowledge/`, or `Meetings/` with a summary at the top, and `references/documents-index.md` is updated.

**The wow moment:** *"Ask me what I should focus on this week."* — response cites your boss's priorities, competitors, ingested PRDs, and active projects.

---

## When NOT to run this

- Single-file update → edit directly or `/ingest-document`
- New tool only → `connections.md`
- System health → `/health-audit`

---

## Execution

### Step 1: Check what's already filled

Read `CLAUDE.md`, `GOALS.md`, `references/product-context.md`, `references/documents-index.md`, `references/platform.md`, `references/voice.md`, `connections.md`.

- **All filled** → offer refresh or section update
- **Partial** → resume from next unanswered question
- **Fresh clone** → welcome:

> "Welcome to Mahip PM-OS. I'll ask questions **one at a time** — about you, your boss, competitors, team, and product. Then we'll **upload your documents** (PRDs, roadmaps, research). Each upload gets saved to the right folder and summarized automatically.
>
> Takes about 20–30 minutes. On Cowork, keep this folder as your workspace.
>
> Ready? Let's start."

---

### Step 2: The interview

**Rules:**
- One question at a time. Explain why + give an example. Reflect answer back.
- Write to files as you go (resumable if interrupted).
- Adapt examples to persona from Q1.

**Persona adaptations:**
| Persona | Emphasize in Q3–Q5, Q12 |
|---------|-------------------------|
| PM | Product users, feature OKRs |
| CPO / Head of Product | Portfolio, multi-product |
| CSO / COO | Client engagements (`Engagements/` per EXPANSIONS.md) |
| CTO | Platform, eng capacity |
| CEO | Company priorities, board metrics |

---

**Q0 — Platform**

> "How will you mostly use this? **Claude Cowork**, **Claude Code**, **Cursor**, or a mix?"

→ `references/platform.md`

---

**Q1 — Persona**

> "Which describes you best? **PM**, **CPO / Head of Product**, **CSO / COO**, **CTO**, **CEO**, or **Other**?"

→ `GOALS.md`, `CLAUDE.md` role

---

**Q2 — Who are you and what do you build?**

> "Name, title, company, product (or portfolio) one-liner. Example: 'Priya, Senior PM at Acme, AI scheduling for clinic admins.'"

→ `CLAUDE.md` identity

---

**Q3 — Users and core problem**

> "Who uses your product (or who are your clients), and what pain do they have? Be specific — picture one person on a bad Tuesday."

→ `CLAUDE.md` product context, `GOALS.md` what I own

---

**Q4 — Quarterly priorities (2–3)**

> "What must happen this quarter? Numbers and dates, not themes. Example: 'Ship AI summaries by June, cut onboarding drop-off 60%→40%.'"

→ `GOALS.md` OKRs

---

**Q5 — North star and guardrail**

> "One product metric that captures success, and one floor you can't break. Example: 'North star: weekly active users completing core task. Guardrail: P95 latency under 2s.'"

→ `CLAUDE.md`, `references/product-context.md` metrics table if baseline given

---

**Q6 — Your boss / manager** *(required)*

*Why:* Stakeholder briefs and weekly focus must align with what your manager cares about.

> "Tell me about your **direct manager** (or skip-level if that's who you report into for product):
> - Name and title
> - What they care about most (metrics, risk, velocity, customers?)
> - How they want updates (async doc, bullets, live meeting, data-first?)
> - What annoys them or what to avoid
>
> Example: 'Ankit, VP Product — cares about activation and enterprise pipeline. Wants a 3-bullet Slack every Friday, hates surprises. Lead with the number, then the ask.'"

Capture as first row in `GOALS.md` Key Stakeholders with `Relationship: Manager`. Also write a short `## Your manager` block at top of stakeholders section.

*If no traditional manager (CEO/founder):* capture board lead, CPO, or primary exec sponsor the same way.

---

**Q7 — Other key stakeholders (3–5)** *(required)*

> "Besides your manager — eng lead, design partner, data, GTM, key customer sponsor. For each: name, role, how they communicate, one note."

→ `GOALS.md` stakeholder table

---

**Q8 — Competitors** *(required)*

*Why:* Competitive analysis and positioning need names, not generics.

> "Who are your **2–4 main competitors** (or alternatives — including 'do nothing' or spreadsheets)?
> For each: name, what they're known for, where you're stronger, where they're stronger.
>
> Example: 'Notion — flexible docs, weak on structured PM workflows. We're stronger on roadmap-to-execution traceability.'
>
> If you have a competitive doc, say 'I'll upload it in the next step' — don't paste everything now."

→ `references/product-context.md` competitors table
→ If detailed answer: `Knowledge/competitors/_overview.md` with summary bullets

---

**Q9 — Voice samples** *(required — paste only)*

> "Paste 1–2 things you wrote recently **as-is** — Slack, email, PRD paragraph. Don't rewrite. One internal, one external if possible."

**Hard rule:** refuse freshly composed text. → `references/voice.md` + 3 voice observations

---

**Q10 — Tools**

> "Tools you use daily: task tracker, email, docs, analytics DB, design, etc. Names only — no passwords."

→ `connections.md` (all `Status: planned` unless user says wired)

---

**Q11 — Document upload** *(required phase — loop until done)*

*Why:* PRDs and research should live in the folder, summarized, indexed — not only in chat memory.

> "Now let's add your **documents**. Upload or paste anything you have — I'll save each one to the right place and write a summary automatically.
>
> **What to upload (any you have):**
> - PRDs / specs
> - Roadmaps or strategy decks
> - User research or interview notes
> - Competitive battlecards or market notes
> - OKR docs, metric dashboards, meeting notes
>
> **How:** Attach files in Cowork, paste content, or point to `@Projects/...` if already in the folder.
>
> Upload one or many. Say **'done'** when finished. Say **'skip'** only if you truly have zero docs."

**For each upload — run ingest-document immediately:**

1. Apply `_Registry/document-routing.md`
2. Save file with `## Summary` + `## Key facts for PM-OS` + `## Full content`
3. Update `references/documents-index.md`
4. Update `references/product-context.md` relevant table
5. Create `Projects/[slug]/` from `_template/` if PRD implies new project
6. Confirm: *"Saved to [path]. Summary: [one line]. Upload another or say 'done'."*

**Do not** only store uploads in conversation — **always write files**.

When user says **done**:
- If zero docs ingested: note in `product-context.md` "No documents at onboarding — starting fresh"
- Print count: *"Ingested [N] documents. Index at references/documents-index.md."*

---

**Q12 — Active projects (1–3)**

> "What's in flight right now? Name, what done looks like, due date. I'll link these to ingested PRDs if they match."

→ `Tasks/active.md`
→ `Projects/[slug]/brief.md` for top initiative (merge from ingested PRD summary if exists)

---

**Q13 — Terminology**

> "Acronyms and internal names I must get right. Example: 'WAU = weekly active workspaces. Never say dashboard — we call it Command Center.'"

→ `references/product-context.md`, `CLAUDE.md` key terminology

---

**Q14 — Manual weekly grind**

> "Most repetitive task you wish you didn't do every week?"

→ `GOALS.md` working style (seed for `/level-up`)

---

**Q15 — Development goals**

> "2–3 things you're improving as a [persona] this year?"

→ `GOALS.md` personal development

---

### Step 3: Final scaffold pass

Backup to `archives/onboard-backup-{YYYY-MM-DD-HHMM}/` if overwriting filled content.

Verify all files exist and have no `[FILL IN]` in critical sections:

| File | Sources |
|------|---------|
| `CLAUDE.md` | Q2, Q3, Q5, Q13, Q10 |
| `GOALS.md` | Q1–Q8, Q14, Q15 |
| `references/voice.md` | Q9 |
| `references/product-context.md` | Q2, Q3, Q8, Q11, Q12, Q13 |
| `references/documents-index.md` | Q11 ingests |
| `references/platform.md` | Q0, Q10 |
| `connections.md` | Q10 |
| `Tasks/active.md` | Q12 |
| `Projects/[slug]/` | Q11 + Q12 |
| `Knowledge/competitors/` | Q8, Q11 competitive docs |
| `decisions/log.md` | create if missing |

---

### Step 4: Closing screen

```
✓ Setup complete.

Ingested: [N] documents → references/documents-index.md
Manager: [name] — updates via [their style]
Competitors: [names]

Try now:
  "What should I focus on this week?"
  "Write a stakeholder update for [manager name]"
  "/ingest-document" — add more docs anytime

Day 7: health-audit  |  Fridays: level-up
```

**Wow prompt** must cite: one Q4 priority, one Q12 project, manager name from Q6, one competitor from Q8 or one ingested doc from Q11.

---

## Critical rules

1. **Q6, Q7, Q8, Q11 are required** — push back if user tries to skip boss, competitors, or docs (allow Q11 skip only if zero docs exist)
2. **Every upload → ingest-document** — always write files + update indexes
3. **Voice (Q9)** — paste only, no fresh composition
4. **One question at a time** in interview; Q11 allows multiple files in a loop
5. **Never invent** stakeholders, competitors, or doc content
6. **No secrets** in repo
7. **Idempotent** — re-run refreshes; backup before overwrite

---

## Verification

- Q6 → manager row in GOALS.md with communication style
- Q8 → competitors in product-context.md
- Upload PRD in Q11 → `Projects/[slug]/requirements.md` exists with `## Summary` at top + row in documents-index.md
- Wow prompt mentions manager + competitor or ingested doc
