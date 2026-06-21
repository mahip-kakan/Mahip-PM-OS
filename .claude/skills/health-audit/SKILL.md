---
name: health-audit
description: Use when asked "audit my PM-OS", "score my setup", "is my system working", "find gaps in my setup", or "health check". Scores the PM-OS against a Four-Cs framework (0-100) and surfaces the top 3 leverage-weighted gaps with concrete next steps.
---

## What this skill does

Runs the **Four-Cs Audit** on the current Mahip-PM-OS project. Reads (never writes) all system files, scores each of the Four Cs out of 25, and surfaces the top 3 leverage-weighted gaps with concrete one-line next steps.

**Scope is structural** — "is the PM-OS built and filled in correctly?" It does NOT evaluate the quality of your PM work or suggest new skills. Capability gaps ("you should add a competitive-analysis skill") belong to `/level-up`. The audit answers: are the context, connections, capabilities, and cadences in good shape?

Run on Day 7 after `/onboard`. Re-run monthly to watch the score climb.

---

## Today's context

- **Date:** run `date +%Y-%m-%d` to get today's date
- **Project root:** current working directory

---

## The Four Cs (scored 25 each = 100 total)

| Layer | Question it answers |
|-------|---------------------|
| **Context** | Does the PM-OS know who you are, what you're building, and what matters? |
| **Connections** | Can it reach your live tools and data sources? |
| **Capabilities** | Does it have skills to do real PM work? |
| **Cadence** | Does it run without being asked? |

---

## Execution

### Step 1: Discover the project shape

Read these files. Note which sections are filled vs. still contain `[FILL IN]`:

**Context files:**
- `CLAUDE.md` — operating manual (loaded every session)
- `GOALS.md` — identity, ownership, OKRs, stakeholders
- `references/voice.md` — voice samples
- `decisions/log.md` — decision history

**Connections:**
- `connections.md` — tool registry

**Capabilities:**
- `.claude/skills/*/SKILL.md` frontmatter — count + names
- `Templates/` — count files
- `Workflows/` — count files

**Cadence signals:**
- `.claude/settings.json` hooks key (if exists)
- Skill names matching `daily-*`, `weekly-*`, `morning-*`, `standup`
- `Tasks/active.md` — any tasks updated within 7 days?
- `GOALS.md` — OKR statuses updated (not all "Not Started")?

---

### Step 2: Score each C (25 points each)

#### Context (25 pts)

| Criterion | Points | How to detect |
|-----------|--------|---------------|
| CLAUDE.md is substantive (no `[FILL IN]` remaining, >150 words of real content) | 6 | Read CLAUDE.md, count unfilled sections |
| Identity captured — name, role, product, target users all filled | 5 | Check `## Who I Am` section |
| GOALS.md filled — at least one OKR with a real KR (not placeholder) | 5 | Check `## Q[X] OKRs` sections |
| Key Stakeholders table has ≥3 real entries | 4 | Check `## Key Stakeholders` in GOALS.md |
| `references/voice.md` exists with real writing samples | 3 | File exists and has content beyond headers |
| `decisions/log.md` exists with ≥1 real entry | 2 | File exists with content |

#### Connections (25 pts)

A "connected" tool means it appears in `connections.md` with status `active` (not just placeholder rows).

| Criterion | Points | How to detect |
|-----------|--------|---------------|
| `connections.md` exists and has ≥1 real tool entry | 5 | File exists, non-placeholder rows |
| ≥3 tool categories covered (comms, tasks, analytics, design, docs) | 10 | Count distinct categories in connections.md. 2 pts per category. Cap 10. |
| At least one analytics/data tool connected (Amplitude, Mixpanel, Looker, etc.) | 5 | Check connections.md for analytics category |
| At least one write-capable connection (can send message, create ticket, etc.) | 3 | Look for Slack, Linear, Jira, Notion with write access noted |
| Freshness — no tool entry older than 90 days (check "Last checked" column) | 2 | Compare dates in connections.md |

#### Capabilities (25 pts)

| Criterion | Points | How to detect |
|-----------|--------|---------------|
| Core 10 skills installed (count `.claude/skills/*/SKILL.md`) | 10 | 1 pt per skill. Cap 10. |
| At least 1 Template used (file has content beyond headers) | 5 | Read a file in `Templates/` — does it have real content filled in? |
| At least 1 Workflow has been run (file has "Last run:" note or session notes added) | 5 | Check `Workflows/` files for usage evidence |
| `_Registry/skill-index.md` up to date (lists all installed skills) | 3 | Compare skill-index entries vs. actual skill folders |
| At least 1 project active (`Projects/` has a non-template subfolder) | 2 | Count non-`_template` subdirs in `Projects/` |

#### Cadence (25 pts)

| Criterion | Points | How to detect |
|-----------|--------|---------------|
| `Tasks/active.md` has ≥1 task with a due date in the next 14 days | 7 | Read active.md |
| OKR statuses in GOALS.md are not all "Not Started" (shows active tracking) | 7 | Check status fields in GOALS.md |
| `Workflows/weekly-review.md` has been referenced recently (any timestamp or note) | 5 | Check for "Last run" or session note in file |
| Hooks configured OR skill named `daily-*`/`weekly-*`/`standup` exists | 3 | Check settings.json + skill names |
| `Experiments/active.md` has at least one live experiment | 3 | Read active.md for real content |

---

### Step 3: Identify top 3 gaps by leverage

For each criterion that lost points: **leverage = points lost × impact multiplier**.

**Impact multipliers:**
- CLAUDE.md still has `[FILL IN]` sections: **4×** (every session is degraded)
- GOALS.md has no real OKRs: **4×** (no strategic anchor for prioritization)
- No `references/voice.md`: **3×** (all external communications sound generic)
- 0 tools in `connections.md`: **3×** (PM-OS is flying blind)
- No analytics tool connected: **3×** (can't do data-driven PM work)
- ≤3 skills installed: **2×** (limited PM-OS capability)
- Tasks/active.md is empty or stale: **2×** (no operational grounding)
- No Key Stakeholders filled: **2×**
- `decisions/log.md` missing or empty: **1.5×**
- Workflows never used: **1.5×**
- All others: **1×**

Sort gaps by leverage descending. Take top 3. For each, write a one-line concrete next step:
- **CLAUDE.md unfilled** → "Run `/onboard` to auto-fill all `[FILL IN]` sections."
- **No GOALS.md OKRs** → "Fill in `GOALS.md → Q[X] OKRs` with this quarter's objectives and key results."
- **No voice.md** → "Run `/onboard` and answer Q6 — paste 2 raw writing samples."
- **No connections.md** → "Run `/onboard` and answer Q7 — list your daily tools."
- **No analytics tool** → "Add your analytics tool (Amplitude/Mixpanel/Looker) to `connections.md`."
- **Stale tasks** → "Update `Tasks/active.md` — any item not touched in 7 days needs a status."

---

### Step 4: Output the report

Print directly in chat. Format:

```
# PM-OS Health Audit — {date}
**Score: {total}/100** — {stage}

Stage thresholds:
  0–39  → Stage 0: Not Yet Running
  40–69 → Stage 1: Operational
  70–89 → Stage 2: Compounding
  90–100 → Stage 3: High-Performance

## Scoreboard

Context        {bar}  {n}/25  {label}
Connections    {bar}  {n}/25  {label}
Capabilities   {bar}  {n}/25  {label}
Cadence        {bar}  {n}/25  {label}

(bar = █ per 5pts; label = "Strong" ≥20, "Solid" 15–19, "Thin" 8–14, "Missing" <8)

## Strengths
- {1–3 short bullets from highest-scoring criteria}

## Top 3 Gaps (ranked by leverage)
1. **{gap name}** (–{points} × {multiplier}× = {leverage score})
   → {concrete one-line next step}
2. **{gap name}** (–{points} × {multiplier}× = {leverage score})
   → {concrete one-line next step}
3. **{gap name}** (–{points} × {multiplier}× = {leverage score})
   → {concrete one-line next step}

## Suggested next: {single most leveraged action in one sentence}

---
Structural gaps only. For automation and capability gaps (what your PM-OS could
DO that it can't yet), run /level-up after this audit.
```

---

### Step 5: Offer to save the report

After printing, ask: "Save this to `audits/audit-{date}.md` so you can track your score over time?" If yes, write the file (create `audits/` folder if needed). This is the only writable side effect.

---

## Notes

- **Read-only by default.** Never modify CLAUDE.md, GOALS.md, skills, or any project files. Only optional write is the audit report.
- **Be flexible about fill-in state.** A section with real content but imperfect formatting still counts as filled.
- **Be honest, not generous.** A 90/100 is rare. Most setups land 40–70 on first run.
- **Don't penalize for unfilled template files.** `Projects/_template/` is scaffold, not content.
- **Speed matters.** Report in under 60 seconds. Read frontmatter only for skills, don't read full skill bodies.
