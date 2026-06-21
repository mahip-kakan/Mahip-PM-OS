---
description: Summarize a meeting transcript into structured notes with decisions and action items
argument-hint: "<transcript, rough notes, or paste>"
---

# /meeting-notes — Meeting Summary

Apply **summarize-meeting** and save to your PM-OS folder structure.

**Before starting:** Read `GOALS.md` stakeholder table to name participants correctly.

## Invocation

```
/meeting-notes [paste transcript]
/meeting-notes [upload file]
```

## Workflow

### Step 1: Accept input

Transcript (Otter, Fireflies, Meet, Zoom), rough notes, or audio summary.

### Step 2: Structure

Apply **summarize-meeting** — participants, decisions, action items, open questions.

Match action owners to names in `GOALS.md` when possible.

### Step 3: Save

Save to `Meetings/[YYYY-MM-DD]-[topic].md`.

Significant decisions → append to `decisions/log.md`.
Action items → append to `Tasks/active.md` (ask before writing).

### Step 4: Offer follow-ups

- "Draft a **stakeholder brief** from these decisions?" → `stakeholder-brief`
- "Prep an **interview script** for the open question?" → `interview-script`

## Notes

- Distinguish "discussed" vs "decided"
- Action items without owners get flagged, not invented
