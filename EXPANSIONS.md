# EXPANSIONS — What to Add as You Grow

This system ships lean on purpose: 25 skills, 4 commands, defined folders, clear responsibilities. As you use it, you'll outgrow the base. This guide tells you what to add, when, and why — and what NOT to add so you don't rot the structure.

**The structure should look like a well-run PM's workspace, not a hoarder's Notion.**

---

## What Ships in the Kit (Don't Remove)

| File / Folder | Purpose |
|---------------|---------|
| `CLAUDE.md` | Session entry point. Loaded automatically every conversation. |
| `GOALS.md` | Identity, ownership, OKRs, stakeholders. The strategic anchor. |
| `connections.md` | Registry of every tool/integration the PM-OS can reach. |
| `references/voice.md` | Raw writing samples for voice matching on communications. |
| `references/product-context.md` | PRDs, roadmaps, terminology, baselines, competitors — populated by `/onboard` and `/ingest-document`. |
| `references/documents-index.md` | Master index of every ingested document. |
| `references/platform.md` | Cowork vs Code setup, MCP safety preferences. |
| `_Registry/document-routing.md` | Rules for where uploads are saved. |
| `decisions/log.md` | Append-only record of decisions and rationale. |
| `Tasks/` | Active work, backlog, archive. Operational ground truth. |
| `Projects/` | One-off initiatives with brief, requirements, decisions. |
| `Workflows/` | Repeatable processes you run many times. |
| `Meetings/` | Notes by meeting. |
| `Knowledge/` | Persistent reference across all projects. |
| `Experiments/` | Active A/B tests and results. |
| `Templates/` | Blank document skeletons. |
| `.claude/skills/` | 25 skills — core PM, discovery, data, meta (onboard, health-audit, level-up). |
| `.claude/commands/` | 5 slash workflows: discover, red-team-prd, analyze-test, meeting-notes, ingest-document. |
| `_Registry/` | Skill index and system health checklists. |

---

## What to Add as You Grow

| Addition | Add when | Why |
|----------|----------|-----|
| `audits/` folder | After running `/health-audit` for the first time | Stores dated audit reports so you can track your score over time |
| `references/{tool}-api.md` | You wire in a new API (Amplitude, Linear, etc.) | Researched-once-saved-forever. `/health-audit` rewards this. Future skills don't re-research the same API. |
| `scripts/` folder | You write a Python or JS script to hit an API not covered by MCP | Most second connections are scripts, not MCPs. Keep them here so Claude knows where to look. |
| `Knowledge/competitors/` files | After running `competitive-analysis` on a competitor | Saves findings for future reference — `/health-audit` checks freshness. |
| `Knowledge/users/` files | After running `user-research` with real interview notes | Persistent user insight that persists beyond a single project. |
| `.claude/rules/` files | A rule gets too long or too scoped for `CLAUDE.md` | Move detailed rules out of `CLAUDE.md` to keep it under 120 lines. |
| `Meetings/1on1s/` subfolder | You have recurring 1:1s worth tracking | Create only when you have actual notes to put there. |
| Sub-OS folders (e.g. `launch-os/`) | A major initiative needs its own scoped workflow context | Isolation pattern — large initiatives get their own operating manual + focused skills. |

---

## Suggested Cadences

| File / Folder | When to touch |
|---------------|---------------|
| `decisions/log.md` | Every time a significant trade-off is made. Claude prompts you. |
| `connections.md` | Every time a new tool is wired in. Add a row, update "Last checked." |
| `Tasks/active.md` | Daily or after every session with meaningful work. |
| `GOALS.md` | When OKR status changes, or quarterly for a full refresh. |
| `CLAUDE.md` | Quarterly prune — every rule must earn its place. Run `/health-audit` first. |
| `_Registry/skill-index.md` | Every time a new skill is added via `/level-up`. |
| `audits/` | Monthly — save the `/health-audit` report to track progress over time. |
| `references/voice.md` | Every 6 months, or when your communication style has shifted (new job, new audience). |

---

## What NOT to Add

Anti-patterns that look helpful but rot the structure:

- **Don't dump raw meeting transcripts into `Knowledge/`.** Interpreted insights only. If you can't summarize the key finding in 3 bullets, it doesn't belong in evergreen knowledge.
- **Don't create `notes/`, `misc/`, `tmp/`, or `scratch/` folders.** Graveyards. If it's important, put it in the right folder. If it's not, don't save it.
- **Don't add more skills before deepening the ones you have.** A skill you use 3x/week beats three skills you've used once. Run `/level-up` to discover skills that match real usage patterns — don't install them speculatively.
- **Don't pre-create `Meetings/` subfolders.** Create `Meetings/1on1s/` only when you have the first note to put there. Empty folders are noise.
- **Don't fork `CLAUDE.md`.** One root `CLAUDE.md`. Sub-OS folders can have scoped versions, but the root is canonical. Never have two competing CLAUDE.md files at the same level.
- **Don't add parallel decision logs.** One `decisions/log.md` at the root captures system-level decisions. Per-project decisions go in `Projects/[name]/decisions.md`. Never have both at the root.
- **Don't over-template.** Templates define output structure. If you find yourself adding a template for every possible document type, you're avoiding the work of thinking about what output should look like. Use templates for documents you produce repeatedly with consistent structure.

---

## How to Tell When It's Time to Add Something

Ask three questions:

1. **Is this conceptually new?** Or does it fit somewhere that already exists?
2. **Will I touch this 3+ times in the next month?** If not, it's premature.
3. **Would a future skill naturally route output here?** If yes, the system will use it. If no, you're organizing for yourself, not for the system.

Two yeses = add. One yes = wait. Zero = don't add.

---

## Token Budget Guidance

`CLAUDE.md` is loaded every session. Keep it under 120 lines.

When a rule or section grows beyond 5–6 lines, move it to `.claude/rules/[topic].md`. Reference it from CLAUDE.md with one line: `See .claude/rules/[topic].md for detailed guidance on [topic].`

This keeps session startup cost low while preserving full depth when needed.

---

> *The structure should look like a well-run PM's workspace. When you can't find something quickly, that's a signal to consolidate — not to add another folder.*
