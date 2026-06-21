---
description: Ingest an uploaded or pasted document — classify, summarize, save to the right folder, update indexes
argument-hint: "<upload file, paste content, or @path>"
---

# /ingest-document — Save & summarize a document

Apply **ingest-document** skill. Use anytime after setup — not only onboarding.

## Invocation

```
/ingest-document [attach file]
/ingest-document @Projects/draft-prd.pdf
/ingest-document [paste content] — this is our competitor battlecard
```

## Workflow

1. Read `_Registry/document-routing.md`
2. Classify document type (ask once if unclear)
3. Save to correct folder with Summary + Key facts + Full content
4. Update `references/documents-index.md` and `references/product-context.md`
5. Scaffold `Projects/[slug]/` if PRD implies new initiative
6. Confirm path and 2-sentence summary

## Notes

- Works in Cowork (upload), Claude Code, and Cursor
- Re-ingesting same doc refreshes summary and full content
- Say "ingest all attachments" if multiple files uploaded at once
