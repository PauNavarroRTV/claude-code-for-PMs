---
name: acceptance-criteria
description: Write acceptance criteria for a WLA feature in GIVEN/WHEN/THEN format. Use when the user asks to write AC, acceptance criteria, or test conditions for a feature or user story. Always embedded inside a Functional Definition — no standalone publishing.
when_to_use: Triggered by 'acceptance criteria', 'AC', 'write AC', 'test conditions', 'given when then'. Always load format-guardrails.md before producing output.
argument-hint: "<feature or user story description>"
---

# Acceptance Criteria

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `pm-uploaded-knowledge/product/product-definition.md` — for behavioral expectations by monetisation mode (Section 8)
3. Load `pm-uploaded-knowledge/product/tech-stack.md` — for technical constraints

You are writing AC for: **$ARGUMENTS**

---

## Format

```
GIVEN [precondition — the system or user state before the action]
  WHEN [action — what the user does or what event occurs]
  THEN [expected outcome — observable system behaviour]
  AND [additional outcome if needed]
```

---

## Steps

1. **Group AC by feature area** — e.g. "Page Display", "Metadata Rendering", "CTA Buttons", "Error States", "Skeleton States"
2. **For each AC:**
   - GIVEN = specific precondition (not vague like "the user is logged in" unless auth is relevant)
   - WHEN = a single action or event, not a sequence
   - THEN = one observable, testable outcome
   - AND = additional outcomes from the same trigger (max 3 per AC before splitting)
3. **Quality checks:**
   - Each AC is independently testable
   - No implementation detail (no "the API returns...", "the component renders...")
   - Cover happy path, edge cases, and error states
   - Negative cases (what does NOT happen) belong in DON'Ts, not AC

---

## Edge Case Checklist

Always consider:
- What happens when metadata is missing or null?
- What happens on slow network / timeout?
- What happens on first visit vs. returning user?
- What happens on different devices if scope is multi-device?
- What is the empty state?
- What is the loading/skeleton state?

---

## Notes

- Acceptance criteria are always embedded inside the FD document — no standalone Confluence publishing
- Resume and Restart are out of scope until user authentication is in place
- For playback AC, always specify which content types are in scope (AVOD, SVOD, TVOD, FAST)
