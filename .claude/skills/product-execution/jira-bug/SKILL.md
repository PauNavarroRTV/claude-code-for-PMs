---
name: jira-bug
description: Create a Jira bug report on the WLA board. Use when the user asks to report a bug, file a defect, or create a bug ticket. Applies all WLA field defaults and the full bug ADF description template including environment, steps to reproduce, current and expected behaviour, device info, and resources.
when_to_use: Triggered by 'jira bug', 'bug report', 'file a bug', 'report a defect', 'create a bug'. Always load format-guardrails.md and team-tools.md before creating.
argument-hint: "<bug title or description>"
allowed-tools: mcp__atlassian__createJiraIssue mcp__atlassian__searchJiraIssuesUsingJql
---

# Jira Bug Report

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `pm-uploaded-knowledge/organization-team/team-tools.md` — for all IDs and field values

You are reporting: **$ARGUMENTS**

---

## Field Defaults (WLA Board)

| Field | Required | Default | Notes |
|---|---|---|---|
| Summary | Yes | — | Always fill — never leave blank |
| Issue Type | Yes | Bug | — |
| Description | Yes | — | Use ADF bug template below |
| Components | Yes | — | Ask user: CTV, Mobile, Roku, Web (multi-select) |
| Reporter | Yes | Pau Navarro | Account ID: `712020:28967fca-28f0-4384-9156-5993ad5d94de` |
| Priority | Yes | Minor (ID: 4) | Always set unless user specifies otherwise |
| Planning Type | Yes | Planned (`{"id": "11283"}`) | Field ID: `customfield_12516` |
| Parent | No | Empty | Leave unset unless user specifies |
| Sprint | No | Empty | Leaves ticket in Backlog unless user specifies |
| Label | No | `claude-code-generated` | Always apply when creating via MCP |

---

## ADF Bug Description Template

Render as ADF when creating via MCP:

```
🧑 Summary
[Provide as much detail as possible]

🌎 Environment
[Production / dev environment / branch / version]
[Mobile only: Build number | Geo Market (optional) | Application (Release/Spartan)]

🐞 Steps to Reproduce
1. [Step 1]
2. [Step 2]
3. [Step 3]

🐞 Current Behaviour
[What is happening now]

✨ Expected Behaviour
[What should happen — per FD, TD, or Business Rules]

📱 Device Information
[Model / OS Version / Year]

📎 Resources
[Videos, images, log files — if available]
```

---

## Steps

1. Gather bug details: what happened, on which device, which environment, steps to reproduce
2. Draft the bug report using the ADF template above
3. Show the drafted ticket to Pau for review
4. Ask: "Would you like me to create this bug report directly in Jira?"
5. If yes: use `mcp__atlassian__createJiraIssue`
   - Cloud ID: `a3ca619b-8171-49e9-890f-0d11e17e9bb7`
   - Project key: `WLA`
   - Issue type: Bug

---

## MCP Usage

- `mcp__atlassian__createJiraIssue` — create the bug ticket
- `mcp__atlassian__searchJiraIssuesUsingJql` — check for duplicate bugs before creating
- Connection details in `pm-uploaded-knowledge/organization-team/team-tools.md`
