# Quickstart — Mahip PM-OS

Get fully operational in 15–20 minutes.

---

## Choose your platform

| Platform | Start here |
|----------|------------|
| **Claude Code** | Steps below |
| **Claude Cowork** | [`docs/setup-cowork.md`](docs/setup-cowork.md) |
| **Cursor** | Clone repo → copy `.claude/skills/` to `.cursor/skills/` → add rules from `CLAUDE.md` |

---

## Automated setup (recommended)

### Before you start, gather:

- [ ] Your name, role, company, product one-liner
- [ ] Quarterly priorities (2–3 concrete outcomes)
- [ ] North star metric + guardrail
- [ ] **Your boss** — name, what they care about, update format/cadence
- [ ] 3–5 other stakeholders and how they communicate
- [ ] **2–4 competitors** and your differentiation
- [ ] **1–2 writing samples** (paste raw — Slack, email, PRD paragraph)
- [ ] **Documents to upload** — PRDs, roadmaps, research (files to attach in Cowork)
- [ ] What you're actively working on (1–3 initiatives)
- [ ] Tools you use (Jira, Gmail, analytics DB, etc.) — names only, no credentials

### Run onboarding

1. Open Claude Code in this folder (`claude`) **or** open folder in Cowork
2. Say: **"onboard me"**

The wizard asks questions **one at a time**, then a **document upload phase**:
- Platform + persona (PM, CPO, CSO, CTO, CEO)
- Identity, users, OKRs, metrics
- **Boss/manager**, stakeholders, **competitors**
- Voice samples + tools
- **Upload documents** — each auto-saved, summarized, indexed (`/ingest-document`)
- Active projects + terminology
- Growth goals

**Files created/updated:**
- `CLAUDE.md`, `GOALS.md`
- `references/voice.md`, `references/product-context.md`, `references/documents-index.md`, `references/platform.md`
- `connections.md`, `Tasks/active.md`, `Projects/[slug]/brief.md`

When done: *"Ask me what I should focus on this week."*

---

## Wire MCPs (optional, after onboarding)

Update `connections.md` with your tools. Wire locally — never commit secrets.

```bash
claude mcp add [your-jira-mcp]
claude mcp add [your-gmail-mcp]
claude mcp add [your-analytics-db-mcp]
```

Mark rows `Status: active` after verifying. See generic template in `connections.md`.

**Safety defaults:** Email = draft only. DB = read-only. Jira = read unless you ask to create tickets.

---

## Try these first

```
What should I focus on this week?
Write a PRD for [feature]
/discover [feature idea]
/red-team-prd @Projects/my-feature/requirements.md
/ingest-document [attach new PRD]
/meeting-notes [paste transcript]
Define metrics for [feature]
```

---

## Quick reference

| Say this | Claude does this |
|----------|-----------------|
| `onboard me` | 14-question personalized setup |
| `audit my setup` | Score PM-OS 0–100 |
| `level up` | Find one workflow to automate |
| `/discover [idea]` | Full discovery cycle |
| `/red-team-prd [doc]` | Stress-test assumptions |
| `/analyze-test [results]` | A/B test interpretation |
| `/meeting-notes [transcript]` | Structured meeting summary |
| `write a PRD for [X]` | Full PRD via prd-writer |
| `scope this AI feature` | ai-feature-scoper |

Full index: `_Registry/skill-index.md`

---

## Recommended cadence

| When | What |
|------|------|
| Day 1 | `onboard` |
| Day 7 | `health-audit` |
| Every Friday | `level-up` + `Workflows/weekly-review.md` |
| Monthly | Re-run `health-audit`, update `connections.md` |
| Quarterly | Refresh `GOALS.md` OKRs, prune `CLAUDE.md` |

---

## Troubleshooting

**Claude doesn't know my context** → Re-run `onboard`. Confirm workspace is the PM-OS folder.

**Skills not triggering** → Try explicit: "Use the prd-writer skill to write a PRD for X"

**Commands don't work** → Ensure `.claude/commands/` exists. On Cowork, folder must be the workspace root.
