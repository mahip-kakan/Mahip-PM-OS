# Document Routing Rules

When a user uploads or pastes a document, `ingest-document` (or onboarding Q11) routes it automatically.

## Routing table

| Document type | Full content saved to | Summary block | Index updates |
|---------------|----------------------|---------------|---------------|
| **PRD / spec** | `Projects/[slug]/requirements.md` | Top of same file under `## Summary` | `references/product-context.md`, `references/documents-index.md` |
| **Project brief** | `Projects/[slug]/brief.md` | Top of same file | Same |
| **Roadmap / strategy** | `Knowledge/roadmaps/[slug].md` | Top of same file | `product-context.md` roadmap table |
| **User research / interviews** | `Knowledge/users/[slug].md` | Top of same file | `product-context.md` research table |
| **Competitive intel** | `Knowledge/competitors/[competitor-slug].md` | Top of same file | `product-context.md` competitors table |
| **OKR / goals doc** | `Knowledge/strategy/[slug].md` | Extract into `GOALS.md` OKRs if applicable | `documents-index.md` |
| **Meeting notes** | `Meetings/[YYYY-MM-DD]-[topic].md` | Top of same file | `documents-index.md` |
| **Metrics / dashboards** | `Knowledge/metrics/[slug].md` | Baselines → `product-context.md` metrics table | `documents-index.md` |
| **Unknown / mixed** | `Knowledge/inbox/[YYYY-MM-DD]-[slug].md` | Top of same file | `documents-index.md` |

## Slug rules

- Lowercase, hyphenated from title: `Onboarding Step 3 PRD` → `onboarding-step-3-prd`
- Competitor name: `Acme Corp` → `acme-corp`
- Date prefix for inbox only when type is unknown

## Every ingested file must include

```markdown
---
source: uploaded | pasted | @path
original_filename: [if known]
ingested: YYYY-MM-DD
type: prd | roadmap | research | competitive | strategy | meeting | metrics | other
project_slug: [if applicable]
---

## Summary
[5–10 bullets — what this doc is, key decisions, metrics, open questions]

## Key facts for PM-OS
[Structured: stakeholders mentioned, dates, metrics with numbers, terminology, risks]

## Full content
[Converted markdown from upload/paste — or link to @path if already in repo]
```

## After ingest — always update

1. `references/documents-index.md` — one row per document
2. Relevant section of `references/product-context.md`
3. `Projects/[slug]/brief.md` — if PRD implies a project not yet scaffolded, create folder from `_template/`
