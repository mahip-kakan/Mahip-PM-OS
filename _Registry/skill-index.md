# Skill Index

*Quick reference for all 26 skills and 5 commands in Mahip PM-OS.*

---

## System Meta Skills

### onboard
**What it does:** Full setup interview — boss, competitors, stakeholders, voice, tools, **document upload loop** (auto-summarize via ingest-document), active projects. Auto-fills all context files.
**Trigger:** "Set me up" / "Onboard me" / "Let's get started"
**Path:** `.claude/skills/onboard/SKILL.md`

### ingest-document
**What it does:** Classify upload/paste → save to correct folder with summary → update `documents-index.md` and `product-context.md`. Used in onboarding and anytime after.
**Trigger:** "Ingest this" / "Save this upload" / attach file / `/ingest-document`
**Path:** `.claude/skills/ingest-document/SKILL.md`

### health-audit
**What it does:** Scores PM-OS 0–100 across Four Cs. Top 3 leverage-weighted gaps.
**Trigger:** "Audit my setup" / "Score my PM-OS" / "Health check"
**Path:** `.claude/skills/health-audit/SKILL.md`

### level-up
**What it does:** Weekly automation discovery. One run = one scoped artifact shipped.
**Trigger:** "Level up" / "What should I automate" / Friday ritual
**Path:** `.claude/skills/level-up/SKILL.md`

---

## Commands (slash workflows)

| Command | Chains | Saves to |
|---------|--------|----------|
| `/discover` | assumptions → prioritize → experiments | `Projects/.../discovery-plan.md` |
| `/red-team-prd` | strategy-red-team | `Projects/.../red-team-[date].md` |
| `/analyze-test` | ab-test-analysis | `Experiments/active.md` |
| `/meeting-notes` | summarize-meeting | `Meetings/` |
| `/ingest-document` | ingest-document | `Projects/`, `Knowledge/`, `Meetings/` + indexes |

Paths: `.claude/commands/` · Routing rules: `_Registry/document-routing.md`

---

## Core PM Skills

| Skill | Trigger (short) | Path |
|-------|-----------------|------|
| `prd-writer` | "Write a PRD for [X]" | `.claude/skills/prd-writer/` |
| `metrics-definer` | "Define metrics for [X]" | `.claude/skills/metrics-definer/` |
| `sprint-planner` | "Plan this sprint" | `.claude/skills/sprint-planner/` |
| `competitive-analysis` | "Analyze competitor [X]" | `.claude/skills/competitive-analysis/` |
| `launch-checklist` | "Pre-launch checklist" | `.claude/skills/launch-checklist/` |
| `user-research` | "Synthesize this research" | `.claude/skills/user-research/` |
| `ai-feature-scoper` | "Scope this AI feature" | `.claude/skills/ai-feature-scoper/` |
| `experiment-designer` | "Design an experiment" | `.claude/skills/experiment-designer/` |
| `roadmap-prioritizer` | "Prioritize these features" | `.claude/skills/roadmap-prioritizer/` |
| `stakeholder-brief` | "Draft executive update" | `.claude/skills/stakeholder-brief/` |

---

## Discovery Skills

| Skill | Trigger (short) | Path |
|-------|-----------------|------|
| `identify-assumptions-existing` | "What are the riskiest assumptions for [X]?" | `.claude/skills/identify-assumptions-existing/` |
| `prioritize-assumptions` | "Prioritize these assumptions" | `.claude/skills/prioritize-assumptions/` |
| `brainstorm-experiments-existing` | "Design experiments to test [assumption]" | `.claude/skills/brainstorm-experiments-existing/` |
| `opportunity-solution-tree` | "Build an OST for [outcome]" | `.claude/skills/opportunity-solution-tree/` |
| `interview-script` | "Prep an interview about [topic]" | `.claude/skills/interview-script/` |
| `summarize-interview` | "Summarize this interview transcript" | `.claude/skills/summarize-interview/` |

---

## Execution & Quality Skills

| Skill | Trigger (short) | Path |
|-------|-----------------|------|
| `strategy-red-team` | "Red-team this PRD" / "Stress-test this plan" | `.claude/skills/strategy-red-team/` |
| `pre-mortem` | "Pre-mortem on [launch]" | `.claude/skills/pre-mortem/` |
| `summarize-meeting` | "Summarize this meeting" | `.claude/skills/summarize-meeting/` |
| `prioritization-frameworks` | "Which framework for this backlog?" | `.claude/skills/prioritization-frameworks/` |

---

## Data Skills

| Skill | Trigger (short) | Path |
|-------|-----------------|------|
| `ab-test-analysis` | "Analyze these A/B test results" | `.claude/skills/ab-test-analysis/` |
| `sql-queries` | "Write a SQL query for [question]" | `.claude/skills/sql-queries/` |

*Requires analytics MCP wired in `connections.md` to run queries against live data.*

---

## When to Use Which

| Situation | Start with |
|-----------|------------|
| Fresh clone | `onboard` (includes document uploads) |
| New PRD / doc uploaded | `/ingest-document` |
| New feature idea (unvalidated) | `/discover` |
| Writing a spec | `prd-writer` (reads `references/product-context.md`) |
| Before eng kickoff | `/red-team-prd` |
| Customer interview prep | `interview-script` |
| After customer interview | `summarize-interview` → `user-research` |
| After any meeting | `/meeting-notes` |
| Experiment ended | `/analyze-test` |
| Need baselines from DB | `sql-queries` |
| Launch prep | `pre-mortem` → `launch-checklist` |
| Prioritization debate | `roadmap-prioritizer` + `prioritization-frameworks` |

---

## Skill Chaining Patterns

**Day 1:** `onboard` → "what should I focus on this week?"

**Discovery → spec:**
`/discover` → `prd-writer` → `/red-team-prd` → `metrics-definer`

**Research loop:**
`interview-script` → `summarize-interview` → `user-research` → `Knowledge/users/`

**New AI feature:**
`ai-feature-scoper` → `prd-writer` → `metrics-definer` → `experiment-designer` → `pre-mortem` → `launch-checklist`

**Experiment lifecycle:**
`experiment-designer` → `Experiments/active.md` → `/analyze-test` → `stakeholder-brief`

**Data-informed PRD:**
`sql-queries` → `prd-writer` → `metrics-definer`

**Launch:**
`pre-mortem` → `launch-checklist` → `stakeholder-brief`

**After meetings:**
`/meeting-notes` → update `Tasks/active.md` → `decisions/log.md`

**System health (monthly):**
`health-audit` → fix top gap → re-run

**Automation (weekly Friday):**
`level-up` → ship artifact → update this index
