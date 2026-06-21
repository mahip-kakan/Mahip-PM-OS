# Setup Guide — Claude Cowork

For PMs and leaders who prefer Claude Cowork over the terminal.

---

## Step 1: Get the folder

**Option A — Git (recommended)**
```bash
git clone https://github.com/mahip-kakan/Mahip-PM-OS.git ~/Mahip-PM-OS
```

**Option B — Download**
Download ZIP from GitHub, unzip to a permanent location (e.g. `~/Documents/Mahip-PM-OS`).

**Option C — Cloud sync**
Copy the folder to Google Drive or Dropbox. Open that path in Cowork so it syncs across machines.

---

## Step 2: Open in Cowork

1. Open **Claude Cowork** (desktop app)
2. Switch to **Cowork** mode
3. Click **Work in a folder** → select your `Mahip-PM-OS` folder (the one with `CLAUDE.md`)
4. Click **Allow** when macOS asks for file access

---

## Step 3: Run onboarding (~20–30 min)

Say: **"onboard me"**

### Interview questions (one at a time)

| Topic | What you'll share |
|-------|-------------------|
| Platform & role | Cowork, PM / CPO / CSO / etc. |
| Product | Users, OKRs, north star metric |
| **Your boss** | Name, what they care about, how they want updates |
| **Stakeholders** | Eng lead, design, data, GTM partners |
| **Competitors** | 2–4 names, strengths/weaknesses vs you |
| Voice | Paste 1–2 real emails/Slack messages |
| Tools | Jira, Gmail, analytics DB, etc. |

### Document upload phase (important)

After the interview, Cowork asks you to **upload documents**:

- PRDs and specs
- Roadmaps and strategy docs
- User research and interview notes
- Competitive battlecards
- OKR docs, metric reports

**What happens when you upload:**

1. Claude **classifies** the doc (PRD, research, competitive, etc.)
2. **Saves** it to the right folder (`Projects/`, `Knowledge/`, `Meetings/`)
3. Writes a **summary at the top** of the file
4. Updates **`references/documents-index.md`** and **`references/product-context.md`**

You don't need to answer questions about the doc — upload and say **"done"** when finished.

**Example paths after upload:**
```
Projects/onboarding-redesign/requirements.md   ← PRD
Knowledge/competitors/acme-corp.md             ← competitive intel
Knowledge/users/interview-batch-march.md       ← research
references/documents-index.md                  ← master index
```

### Add more docs anytime

```
/ingest-document [attach file]
```

---

## Step 4: Wire MCPs (optional)

In Cowork **Customize** → add connectors (Jira, Gmail, Google Drive, etc.).

Update `connections.md` with `Status: active` when verified.

**Safety:** Email = draft only. DB = read-only.

---

## Step 5: Try these prompts

```
What should I focus on this week?
Write a stakeholder update for [your manager's name]
/discover [feature idea]
/ingest-document [attach new PRD]
/red-team-prd @Projects/my-feature/requirements.md
```

---

## How documents work in Cowork

| Action | Result |
|--------|--------|
| Upload during onboarding | Saved to folder + summarized + indexed |
| Upload later in chat | Run `/ingest-document` or say "ingest this" |
| File already in folder | `@Projects/foo/requirements.md` — reference, no re-upload |
| Link only (Notion/Drive) | Stored as reference in `product-context.md`; full text not local unless connector pulls it |

**Rule:** Uploads are **never** chat-only. They always become markdown files in your PM-OS folder.

---

## Troubleshooting

**Claude doesn't know my boss or competitors**
→ Re-run `onboard me` or fill `GOALS.md` (manager) and `references/product-context.md` (competitors).

**Upload didn't save to a file**
→ Say: `/ingest-document` and re-attach. Check `references/documents-index.md`.

**Skills not triggering**
→ "Use the prd-writer skill to write a PRD for X"

**Want more skills later**
→ `/level-up` every Friday to automate a new workflow
