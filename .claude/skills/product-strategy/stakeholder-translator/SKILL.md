---
name: stakeholder-translator
description: Rewrite the same product update in three voices: technical (engineering), outcome-focused (execs), and plain-language (end users or partners). Use when the user asks to translate an update for a different audience, rewrite for stakeholders, or explain something to a specific audience. Saves to output-files/stakeholder-updates/.
when_to_use: Triggered by 'stakeholder update', 'translate for', 'rewrite for', 'explain to', 'simplify for', 'exec version', 'engineering version', 'partner version'. Always load format-guardrails.md and artifact-example.md before producing output.
argument-hint: "<update or message to translate>"
---

# Stakeholder Translator

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `artifact-example.md` (this skill folder)
3. Load `pm-uploaded-knowledge/product/product-definition.md` — for persona goals and communication preferences
4. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are translating: **$ARGUMENTS**

---

## Three Output Voices

### Voice 1 — Technical (Engineering)

**Audience:** Sergio, Nenad, Ferran, Rajaguru, Albert, QA team
**Goal:** Clarity on what to build, technical constraints, and scope boundaries
**Tone:** Precise, implementation-aware, no marketing language
**Format:** What changed, what it affects, technical notes, open questions

```
🔧 Technical Update — [Feature/Change Name]

What changed:
[Specific behaviour delta — what the system does differently]

Affected surfaces:
[CTV / Mobile / Web / Roku / All]

Technical notes:
[Player impact, API changes, config flags, DRM implications if any]

Open questions:
[What needs engineering input before implementation]
```

---

### Voice 2 — Outcome-Focused (Execs / Board)

**Audience:** Sidharth, Osman, Cedric, Hristo, Tristan
**Goal:** Business impact, strategic alignment, risk awareness
**Tone:** Direct, outcome-first, no technical jargon, no feature description
**Format:** Why it matters, what it delivers, what it costs, what's at risk

```
📊 Exec Update — [Feature/Change Name]

What we're doing:
[One sentence — outcome, not feature description]

Why it matters:
[Revenue, retention, or competitive implication]

Expected impact:
[Metric or partner outcome]

Timeline:
[Quarter or sprint reference]

Risk:
[One line — what could go wrong]
```

---

### Voice 3 — Plain Language (Partners / End Users)

**Audience:** Alex (partner business buyer), Emma (end user), discovery prospects
**Goal:** Build confidence, set expectations, no ambiguity
**Tone:** Friendly, benefit-first, zero technical jargon, concrete
**Format:** What's changing, what it means for you, when to expect it

```
📢 Partner/User Update — [Feature/Change Name]

What's new:
[Plain description of the change — no technical terms]

What this means for you:
[Concrete benefit or behavioural change from the partner/user perspective]

When:
[Expected delivery in plain terms — "coming in Q3", "available from July"]

Anything you need to do:
[Action required, or "nothing — this is automatic"]
```

---

## Steps

1. Parse the input update from $ARGUMENTS
2. Identify which voice(s) are needed (default: all three)
3. Produce all three versions without changing the underlying facts
4. Flag any facts in the input that are ambiguous or missing before translating

---

## Output

- Save to `output-files/stakeholder-updates/YYYY-MM-DD_[slug].md`
- No Confluence publishing offer — these are working documents, not formal publications
