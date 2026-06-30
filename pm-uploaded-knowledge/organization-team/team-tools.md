# Team Tools

> Pau-authored. Agent reads, never modifies.
> Source: memory/reference_jira_wla.md
> Always load before any Jira or Confluence MCP operation.

---

## Jira

- **Jira URL:** `https://wuakitv.atlassian.net`
- **Cloud ID:** `a3ca619b-8171-49e9-890f-0d11e17e9bb7`
- **Project Key:** `WLA`
- **Project ID:** `16663`

### Account IDs

| Name | Email | Account ID |
|---|---|---|
| Pau Navarro | pau.navarro@rakuten.com | `712020:28967fca-28f0-4384-9156-5993ad5d94de` |

### Component IDs

| Component | ID |
|---|---|
| CTV | 11479 |
| Mobile | 11481 |
| Roku | 11478 |
| Web | 11480 |

### Custom Fields

| Field | Field ID | Notes |
|---|---|---|
| Planning Type | `customfield_12516` | Required. Planned = `{"id": "11283"}`, Unplanned = `{"id": "11284"}` |
| Story Points | `customfield_10004` | Optional, numeric |
| Sprint | `customfield_10302` | Optional, leave empty for backlog |

### Priority IDs

| Priority | ID |
|---|---|
| Minor (default) | 4 |
| Trivial | 5 |
| Moderate | 10037 |
| Major | 3 |
| Critical | 2 |
| Blocker | 1 |
| Show Stopper/Blocker | 10036 |

### Field Defaults for All Tickets

| Field | Default | Notes |
|---|---|---|
| Reporter | Pau Navarro | Always set unless user specifies otherwise |
| Priority | Minor | Always set unless user specifies otherwise |
| Planning Type | Planned | Always set unless user specifies otherwise |
| Label | `claude-code-generated` | Always apply when creating via MCP |
| Parent | Empty | Leave unset unless user specifies |
| Sprint | Empty | Leaves ticket in Backlog unless user specifies |
| Components | — | Ask user: CTV, Mobile, Roku, Web (multi-select) |

---

## Confluence

- **Space Key:** `WLA`
- **Competitor folder ancestor page ID:** `4897570912`
- **WLA Release Notes page:** Query by title "WLA Release Notes" in WLA space
- **User Stories folder:** Available in WLA Confluence space

---

## MCP Connections

| Tool | Scope | Used for |
|---|---|---|
| Atlassian MCP | WLA Jira + Confluence | Ticket creation, FD publishing, sprint queries, competitor list |
| GitHub MCP | PauNavarroRTV/claude-code-for-PMs | Repo management, file pushes |

---

## Live Queries

**Active Sprint:**
```
project = WLA AND sprint in openSprints() ORDER BY priority ASC
```

**Release Notes:** Query Confluence page titled "WLA Release Notes" in WLA space.

---

## Analytics Tools

<!-- To be populated -->

## Slack

<!-- To be populated -->
