---
name: persona
description: Create a user persona for WLA using the standard persona template. Use when the user asks to create a persona, buyer persona, user profile, or ICP. Covers all demographic, biographical, goal, motivator, challenge, and source-of-information fields. Validates against WLA's four existing personas. Updates ai-generated-knowledge/users/personas.md after creation. Offers Confluence publishing.
when_to_use: Triggered by 'persona', 'user persona', 'buyer persona', 'ICP', 'create a persona'. Always load format-guardrails.md and artifact-example.md before producing output.
argument-hint: "<persona name or role description>"
allowed-tools: mcp__atlassian__createConfluencePage
---

# Persona

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `artifact-example.md` (this skill folder) — contains all four WLA worked examples
3. Load `pm-uploaded-knowledge/product/product-definition.md` — Section 7 (Persona Detail) for existing persona baseline
4. Load `ai-generated-knowledge/users/personas.md` — to check for overlap with existing personas
5. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are creating a persona for: **$ARGUMENTS**

---

## Template

```
Personal quote: ["..."]
Persona name: [Name]
Persona role: [Role]
Job description:
  1. [Responsibility 1]
  2. [Responsibility 2]
  3. [Responsibility 3]
Company: [Name]
Company size: [Size]
Industry: [Industry]
Demographic information:
  Age: [Range]
  Gender: [Gender]
  Income: [Level]
  Education level: [Education]
  Residential environment: [Environment]
Biography: [Bio paragraph — 2-4 sentences covering role, context, and key tensions]
Professional goals:
  - [Goal 1]
  - [Goal 2]
  - [Goal 3]
Motivators:
  - [Motivator 1]
  - [Motivator 2]
  - [Motivator 3]
Challenges:
  - [Challenge 1]
  - [Challenge 2]
  - [Challenge 3]
Sources of information:
  - [Source 1]
  - [Source 2]
  - [Source 3]
```

---

## Steps

1. Identify which persona layer: B2B2C (Emma-type), B2B Business (Alex-type), B2B Integrator (Marco-type), or RTV Internal (Giulia-type)
2. Populate all template fields — no field left blank
3. Personal quote: first-person, captures the persona's core tension
4. Biography: names the role context, key responsibilities, and the friction they face
5. Goals/Motivators/Challenges: minimum 3 each, specific to WLA context
6. Validate: does this persona overlap significantly with an existing one? If yes, flag to Pau before creating

---

## Post-Creation

- Update `ai-generated-knowledge/users/personas.md` with a summary entry
- Save full persona to `output-files/personas/YYYY-MM-DD_[persona-slug].md`
- Ask: "Would you like me to create this User Persona directly in Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`
