---
name: functional-definition
description: Create a Functional Definition (FD) for a WLA product feature. Use when the user asks to write an FD, functional definition, functional spec, or feature specification. Produces the full structured document including summary, user stories, acceptance criteria, DON'Ts, UI interactions, Figma links, and success metrics. Offers Confluence publishing on completion.
when_to_use: Triggered by 'functional definition', 'FD', 'write an FD', 'feature spec', 'functional spec'. Always load format-guardrails.md and artifact-example.md before producing output.
argument-hint: "<feature name or description>"
allowed-tools: mcp__atlassian__createConfluencePage mcp__atlassian__search
---

# Functional Definition

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder) — apply all confirmed rules
2. Load `artifact-example.md` (this skill folder) — use as quality reference
3. Load `pm-uploaded-knowledge/product/product-definition.md` — for platform context and persona validation
4. Load `pm-uploaded-knowledge/product/tech-stack.md` — for technical feasibility
5. Load `pm-uploaded-knowledge/organization-team/team-tools.md` — for Jira/Confluence IDs
6. Apply **Rakuten Reality Audit** per `CLAUDE.md` to the completed FD

You are producing: **$ARGUMENTS**

---

## FD Header

| Field | Value |
|---|---|
| Target Release | [Date] |
| Target Devices | [CTV / Mobile / Web / Roku / All] |
| Jira Epic | [Epic link and status] |
| Signature | NOT SHARED / PENDING / SIGNED OFF |
| Dev Readiness | NOT READY / PRODUCT-READY / DESIGN-READY |
| Product | @Pau Navarro |
| Designer | @[Name] |
| Developer | @[Name] |
| QA | @[Name] |

---

## Steps

1. **Clarify scope** — if $ARGUMENTS is vague, ask: which device(s)? Which monetisation mode? Is this a new feature or a change to existing behaviour?

2. **Summary** — Write a brief overview (3–5 sentences) covering: what the feature does, why it matters, key design decisions, scope boundaries. Reference the relevant persona(s) from `product-definition.md`.

3. **Sign-Off Table** — Include formal review table with columns: Area | Reviewer | Status. Areas: Product, Product Design, Tech, PMO, Ad Tech, BI, Operations, Marketing, Finance, Security, Legal.

4. **User Stories** — Link to relevant user stories per persona:

| User Persona | User Stories |
|---|---|
| [UP] B2B2C Persona (Emma) | [US] links |
| [UP] B2B Persona (Alex/Marco) | [US] links |
| [UP] RTV Persona (Giulia) | [US] links |

5. **Acceptance Criteria** — GIVEN/WHEN/THEN format. Group by feature area. Each AC must be:
   - Specific and testable
   - Scoped to observable behaviour
   - Free of implementation detail

```
GIVEN [precondition]
  WHEN [user action or system event]
  THEN [expected outcome]
  AND [additional outcome if needed]
```

6. **DON'Ts** — Explicit constraints grouped by category: Layout | Metadata & Information | Actions & Playback | Interaction & Navigation | Images/Artwork | General. Each DON'T must be unambiguous.

7. **User Interactions & Designs** — Screen-by-screen interaction flows, skeleton states, layout rules, behavioral specifications. Reference Figma as primary visual source.

8. **Figma Links** — Links to prototypes and screen files.

9. **Success Metrics** — KPI table: Metric | Description | Target Value.

---

## Output

- Save to `output-files/functional-definitions/YYYY-MM-DD_[feature-slug].md`
- Apply Rakuten Reality Audit
- Ask: "Would you like me to create this Functional Definition directly in Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`

---

## MCP Usage

- `mcp__atlassian__createConfluencePage` — to publish to Confluence WLA space
- `mcp__atlassian__search` — to find existing related FDs or user stories
- Connection details in `pm-uploaded-knowledge/organization-team/team-tools.md`
