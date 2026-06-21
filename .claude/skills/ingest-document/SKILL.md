---
name: ingest-document
description: Ingest an uploaded or pasted document — classify it, save to the correct folder, write a summary, and update references/documents-index.md and product-context.md. Use when user uploads a file, pastes a long doc, says "ingest this", "save this PRD", "add this to my knowledge base", or during onboarding document upload.
---

## What this skill does

Takes any document (upload, paste, or `@file` in repo) and:

1. **Classifies** the type (PRD, roadmap, research, competitive, etc.)
2. **Saves** full content as markdown in the correct folder per `_Registry/document-routing.md`
3. **Summarizes** at the top of the file (5–10 bullets + structured key facts)
4. **Updates** `references/documents-index.md` and relevant sections of `references/product-context.md`
5. **Scaffolds** `Projects/[slug]/` if a PRD implies a new initiative

Runs during onboarding (Q11) and anytime after setup.

---

## Execution

### Step 1: Accept input

- File upload (PDF, DOCX, MD, TXT, CSV)
- Pasted text in chat
- `@path/to/file` already in workspace
- User says: "this is our Q2 roadmap" (use as type hint)

If type is unclear, ask once: *"Is this a PRD, roadmap, user research, competitive intel, strategy/OKRs, meeting notes, or something else?"*

### Step 2: Classify and pick destination

Read `_Registry/document-routing.md`. Route to the correct folder and slug.

If user named a project in chat, use that for `project_slug`. Otherwise derive from document title.

### Step 3: Extract content

- **Markdown/text:** use as-is
- **PDF/DOCX:** extract text to markdown; note if formatting was lost
- **Already in repo:** read file; optionally copy to canonical location if currently in inbox/Downloads path

Never invent content. If extraction fails, save what you have + `[NEED: user to re-upload or paste]`.

### Step 4: Write the ingested file

Use the template from `_Registry/document-routing.md`:

```markdown
---
source: uploaded | pasted | path
original_filename: [name]
ingested: [today YYYY-MM-DD]
type: [prd|roadmap|research|competitive|strategy|meeting|metrics|other]
project_slug: [slug or none]
---

## Summary
- [bullet]

## Key facts for PM-OS
**Stakeholders:** ...
**Metrics:** ...
**Decisions:** ...
**Terminology:** ...
**Risks / open questions:** ...

## Full content
[body]
```

### Step 5: Update indexes

**`references/documents-index.md`** — append row:
| Title | Type | Path | Summary (one line) | Ingested |

**`references/product-context.md`** — update the matching table:
- PRD → PRDs and specs table + active initiatives if new project
- Roadmap → roadmap table
- Research → research table
- Competitive → competitors table (+ create `Knowledge/competitors/[slug].md` if not exists)
- Metrics → key metrics baselines table

**`GOALS.md`** — only if document contains OKRs/goals user wants captured (ask if ambiguous)

**`Projects/[slug]/brief.md`** — if PRD/research for a project:
- Create `Projects/[slug]/` from `_template/` if missing
- Merge summary into brief (problem, metrics, constraints from doc — don't overwrite user edits blindly)

### Step 6: Confirm to user

```
✓ Ingested: [title]
  Type: [type]
  Saved: [full path]
  Summary: [2-sentence summary]
  Updated: documents-index.md, product-context.md[, Projects/...]

You can reference this anytime with @[path]
```

If multiple files in one message, ingest each sequentially and confirm each path.

---

## Type-specific extraction priorities

| Type | Pull into summary |
|------|-------------------|
| PRD | Problem, hypothesis, metrics, non-goals, risks, launch date |
| Roadmap | Now/Next/Later themes, deprioritized items, dates |
| Research | Top 3 patterns, surprises, quotes (attributed), sample size |
| Competitive | Strengths, weaknesses, our differentiation, pricing if present |
| Strategy/OKR | Objectives, KRs, baselines, targets |
| Meeting | Decisions, action items, owners |

---

## Rules

- **Always write files** — never only hold upload in chat context
- **Summary first** in every ingested file so future sessions load cheaply
- **One canonical path** per document — no duplicates; update index if re-ingesting same doc
- **Re-ingest:** overwrite `## Full content` and refresh summary; update `ingested` date; note in index
- **Sensitive data:** don't commit secrets; warn user if doc contains credentials
- **Competitors:** each competitor doc → `Knowledge/competitors/[slug].md` AND row in product-context competitors table

---

## Triggers

- "Ingest this document" / "Save this upload"
- "Add this PRD to my project folder"
- User attaches file without other instruction → offer: *"Want me to ingest this into PM-OS?"*
- Onboarding Q11 upload loop
