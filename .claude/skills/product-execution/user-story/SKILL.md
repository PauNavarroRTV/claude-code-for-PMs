---
name: user-story
description: Create user stories for a WLA feature in the standard AS A / I WANT TO / SO THAT format, covering all three personas (B2B2C Emma, B2B Alex/Marco, RTV Giulia). Use when the user asks to write user stories, a story set, or a story table for a feature or epic.
when_to_use: Triggered by 'user story', 'user stories', 'write stories', 'story set', 'story table'. Always load format-guardrails.md and artifact-example.md before producing output.
argument-hint: "<feature name or FD reference>"
allowed-tools: mcp__atlassian__createConfluencePage mcp__atlassian__search
---

# User Story

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `artifact-example.md` (this skill folder)
3. Load `pm-uploaded-knowledge/product/product-definition.md` — for persona goals and JTBD
4. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are writing stories for: **$ARGUMENTS**

---

## Format

Each story follows this structure:

```
Category: [Story Category — e.g. AVOD Content Lists, SVOD Playback, FAST EPG]
User Persona: AS A [role], I WANT TO [action], SO THAT [outcome].
Functional Definition: [Jira/Confluence FD link]
```

---

## Steps

1. **Identify the feature area** from $ARGUMENTS
2. **Produce stories for all three persona layers:**
   - `[UP] B2B2C Persona` — Emma (end user / viewer)
   - `[UP] B2B Persona` — Alex (partner/business buyer) and/or Marco (integrator)
   - `[UP] RTV Persona` — Giulia (internal platform owner)
3. **Format as a table:**

| # | Category | User Persona | User Story | Functional Definition |
|---|---|---|---|---|

4. **Quality checks per story:**
   - Action is specific and observable
   - Outcome is a genuine user benefit, not a feature description
   - Stories do not contain implementation detail
   - Each persona layer has at least 2–3 stories

---

## Persona Colour Coding (for Confluence)

- `[UP] B2B2C Persona` — white/default rows
- `[UP] B2B Persona` — yellow rows
- `[UP] RTV Persona` — grey rows

---

## Output

- Save to `output-files/functional-definitions/YYYY-MM-DD_user-stories-[feature-slug].md`
- Ask: "Would you like me to create these User Stories directly in Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`
