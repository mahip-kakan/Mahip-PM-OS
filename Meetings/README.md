# Meetings

Notes from meetings, organized by type. Action items go to `Tasks/active.md`, not here.

---

## Suggested Structure

Create subfolders as you need them:

```
Meetings/
├── 1on1s/           ← Notes from 1:1s with your manager, reports, or key partners
├── stakeholder/     ← Notes from stakeholder reviews, exec syncs, design reviews
└── team-syncs/      ← Notes from team standups, sprint ceremonies, all-hands
```

**Naming convention:** `YYYY-MM-DD-[person or group].md`

Example: `Meetings/1on1s/2026-05-03-eng-lead.md`

---

## What Goes Here

- Decisions made in the meeting
- Key context shared that Claude should know
- Open questions that need follow-up (move these to `Tasks/active.md` immediately after the meeting)

## What Does NOT Go Here

- Action items (those go in `Tasks/active.md` with an owner and due date)
- Project requirements (those go in `Projects/[name]/requirements.md`)
- Recurring process notes (those go in `Workflows/`)

---

## How Claude Uses This

When you say "I have a meeting with [person] tomorrow," Claude will look here for prior notes with that person. The more consistent your naming, the better it can find relevant history.

When preparing for a recurring meeting, prompt:
> "Read my recent notes in Meetings/[subfolder]/ and help me prepare for tomorrow's [meeting type]."
