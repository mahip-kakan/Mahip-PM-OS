# Connections Registry

Every tool, integration, and data source the PM-OS can reach. Claude references this when asked about data sources, when `/health-audit` scores Connections, and when `/level-up` scopes automations.

*Populated by `/onboard`. Update whenever you wire a new tool. Keep credentials out of this file — wire MCPs locally.*

---

## How to Read This Table

| Column | Meaning |
|--------|---------|
| **Tool** | Name of the tool or service |
| **Category** | What kind of work it supports |
| **Access type** | MCP, API script, or manual export |
| **Can write?** | Yes = create/send/post. No = read-only. Draft = drafts only (e.g. email) |
| **Status** | `active` / `needs-auth` / `manual-only` / `planned` |
| **Last checked** | Date last verified working |
| **Notes** | Auth method, limits, gotchas |

---

## Tool Registry

| Tool | Category | Access type | Can write? | Status | Last checked | Notes |
|------|----------|-------------|------------|--------|--------------|-------|
| [Your task tracker] | Task tracking | MCP | Yes | planned | — | e.g. Jira, Linear, Asana |
| [Your email] | Comms | MCP | Draft only | planned | — | e.g. Gmail — read + draft, never auto-send |
| [Your docs] | Docs / Roadmap | MCP | Yes | planned | — | e.g. Notion, Google Drive, Confluence |
| [Your analytics DB] | Analytics | MCP | No | planned | — | e.g. Postgres, ClickHouse, BigQuery — read-only |
| [Your product analytics] | Analytics | MCP | No | planned | — | e.g. Amplitude, Mixpanel, PostHog |
| [Your chat] | Comms | MCP | Yes | planned | — | e.g. Slack, Teams |
| [Your design tool] | Design | MCP | No | planned | — | e.g. Figma |
| [Your CRM] | Customer data | MCP | No | planned | — | e.g. Salesforce, HubSpot |

*Replace placeholders after `/onboard`. Mark `active` only after verifying the connection works.*

---

## Safety defaults

- **Email:** Draft only — human sends
- **Task trackers:** Read by default — create/update only when explicitly asked
- **Analytics databases:** Read-only queries, row limits, no production writes
- **Never commit** API keys, tokens, or connection strings to this repo

---

## Categories Reference

| Category | Examples |
|----------|----------|
| Task tracking | Jira, Linear, Asana, ClickUp |
| Docs / Roadmap | Notion, Confluence, Google Docs |
| Comms | Slack, Teams, Gmail |
| Design | Figma, Miro |
| Analytics | Postgres, ClickHouse, Amplitude, PostHog |
| Customer data | Salesforce, HubSpot, Intercom |
| Engineering | GitHub, GitLab, Sentry |

---

## Wiring a New Connection

**MCP (recommended):**
```bash
claude mcp add [tool-name]
```
Add a row here with `Access type: MCP`. For Cowork, wire in Cowork settings — see `docs/setup-cowork.md`.

**API script:** `scripts/{tool}_api.py` + `references/{tool}-api.md`

**Manual export:** CSV/JSON on a schedule — note cadence in Notes column

---

## Cadence

- Add a row every time you wire a new tool
- Update "Last checked" when verified
- Review monthly during `/health-audit`
