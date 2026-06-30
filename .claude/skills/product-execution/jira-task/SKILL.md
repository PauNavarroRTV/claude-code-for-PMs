---
name: jira-task
description: Create a Jira task or epic on the WLA board. Use when the user asks to create a Jira ticket, task, story, or epic. Applies all WLA field defaults, ADF description format, story point scale, and the claude-code-generated label. Offers direct Jira creation via MCP.
when_to_use: Triggered by 'jira task', 'jira ticket', 'create a task', 'create a ticket', 'create an epic', 'jira epic'. Always load format-guardrails.md and team-tools.md before creating.
argument-hint: "<task title or description>"
allowed-tools: mcp__atlassian__createJiraIssue mcp__atlassian__getJiraIssue mcp__atlassian__searchJiraIssuesUsingJql
---

# Jira Task

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `pm-uploaded-knowledge/organization-team/team-tools.md` — for all IDs and field values

You are creating: **$ARGUMENTS**

---

## Field Defaults (WLA Board)

| Field | Required | Default | Notes |
|---|---|---|---|
| Summary | Yes | — | Always fill — never leave blank |
| Description | Yes | — | Use ADF template below |
| Components | Yes | — | Ask user: CTV, Mobile, Roku, Web (multi-select) |
| Reporter | Yes | Pau Navarro | Account ID: `712020:28967fca-28f0-4384-9156-5993ad5d94de` |
| Priority | Yes | Minor (ID: 4) | Always set unless user specifies otherwise |
| Planning Type | Yes | Planned (`{"id": "11283"}`) | Field ID: `customfield_12516` |
| Parent | No | Empty | Leave unset unless user specifies |
| Sprint | No | Empty | Leaves ticket in Backlog unless user specifies |
| Label | No | `claude-code-generated` | Always apply when creating via MCP |

---

## ADF Description Template

Render as ADF when creating via MCP:

```
🧑 Summary
[Concise task description — 1-3 sentences]

🌎 Context & Urgency
[Why this is needed and its priority/impact]

🔨 Acceptance Criteria
[Completion criteria — bullet list or GIVEN/WHEN/THEN]

📚 References
[Confluence FD link or relevant documentation]
```

---

## Story Point Estimation

| Points | Level | Description |
|---|---|---|
| 1 | Trivial | Very quick, little to no mental effort |
| 2 | Straightforward | Easy to implement, minimal complexity |
| 3 | Moderate | Takes time, but problem and solution are well understood |
| 5 | High effort | Time-consuming and challenging, but clearly defined and achievable |
| 8 | High uncertainty | Scope or complexity unclear — flag for grooming before sprint commitment |

---

## Steps

1. Draft the task: Summary, description (ADF format), components, priority
2. Show the drafted ticket to Pau for review
3. Ask: "Would you like me to create this ticket directly in Jira?"
4. If yes: use `mcp__atlassian__createJiraIssue`
   - Cloud ID: `a3ca619b-8171-49e9-890f-0d11e17e9bb7`
   - Project key: `WLA`
   - All field IDs from `team-tools.md`

---

## MCP Usage

- `mcp__atlassian__createJiraIssue` — create the ticket
- `mcp__atlassian__searchJiraIssuesUsingJql` — check for existing related tickets before creating
- Connection details in `pm-uploaded-knowledge/organization-team/team-tools.md`
