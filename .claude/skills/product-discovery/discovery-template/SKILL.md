---
name: discovery-template
description: Create a partner discovery template for a WLA prospect or new partner conversation. Use when the user asks to run a discovery session, create a discovery document, scope a new partner, or prepare discovery requirements. Covers Device Coverage, Branding, Monetisation, Authentication, and Integrations. Offers Confluence publishing.
when_to_use: Triggered by 'discovery', 'discovery template', 'discovery session', 'partner discovery', 'prospect discovery', 'scope a partner'. Always load format-guardrails.md and artifact-example.md before producing output.
argument-hint: "<prospect or partner name>"
allowed-tools: mcp__atlassian__createConfluencePage
---

# Discovery Template

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `artifact-example.md` (this skill folder)
3. Load `pm-uploaded-knowledge/product/product-definition.md` — for platform capabilities
4. Load `pm-uploaded-knowledge/product/tech-stack.md` — for device support and DRM
5. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are creating a discovery template for: **$ARGUMENTS**

---

## Header

| Field | Value |
|---|---|
| Discovery Status | DRAFT / TO REVIEW / SUBMITTED |
| Discovery Date | [Date] |
| Discovery Owner | @Pau Navarro |
| Discovery Participants | [Name / Role] |
| Prospect Name | $ARGUMENTS |
| Prospect Website | [URL] |
| Prospect Platform | [Reference OTT platform if any] |

---

## Summary

[Opportunity Summary in 2–3 lines]

- [Device Coverage Summary]
- [Branding & Localization Summary]
- [Content Monetization Summary]
- [User Authentication Summary]
- [Integrations Summary]

---

## Steps

1. **Platform Device Coverage** — For each device type, capture: Required / Not Required + comments
2. **Platform Branding & Localization** — Logo, colours, fonts, splash screen, languages, RTL
3. **Platform Content Monetization** — Content types (Live/VOD), monetisation models (SVOD/TVOD/AVOD/FAST), DRM, ad insertion, geo-blocking
4. **Platform User Authentication** — Auth methods, playback gating, profiles, logged-in features
5. **Integration with Platform Core Components** — For each component: Not Required / Keep / Replace
   - ⚠️ Every time a prospect requires replacing an existing platform component with an RTV managed service, evaluate whether that service will be charged additionally

---

## Device Requirements Table

| # | Device Type | Device OS (OEM) | Required? | Comments |
|---|---|---|---|---|
| 1 | Smart TV | Tizen OS (Samsung) | NOT REQUIRED / REQUIRED | |
| 2 | Smart TV | LG webOS (LG) | NOT REQUIRED / REQUIRED | |
| 3 | Smart TV | Android TV OS (Various) | NOT REQUIRED / REQUIRED | |
| 4 | Smart TV | VIDAA OS (Hisense) | NOT REQUIRED / REQUIRED | |
| 5 | Web | Chrome, Firefox, Safari | NOT REQUIRED / REQUIRED | |
| 6 | Mobile | Android Mobile OS | NOT REQUIRED / REQUIRED | |
| 7 | Mobile | iOS & iPadOS (Apple) | NOT REQUIRED / REQUIRED | |
| 8 | Set-top Box | Android TV OS (Various) | NOT REQUIRED / REQUIRED | |
| 9 | Set-top Box | tvOS (Apple) | NOT REQUIRED / REQUIRED | |
| 10 | Set-top Box | Netgem OS (Netgem) | NOT REQUIRED / REQUIRED | |
| 11 | Streaming Stick | Roku OS (Roku) | NOT REQUIRED / REQUIRED | |
| 12 | Streaming Stick | Fire OS (Amazon) | NOT REQUIRED / REQUIRED | |
| 13 | Console | PS5 OS (Sony) | NOT REQUIRED / REQUIRED | |
| 14 | Console | Xbox OS (Microsoft) | NOT REQUIRED / REQUIRED | |
| 15 | Automotive | webOS Automotive (Kia, Hyundai) | NOT REQUIRED / REQUIRED | |
| 16 | Other | HbbTV | NOT REQUIRED / REQUIRED | |

---

## Monetisation Table

| # | Item | Required? | Comments |
|---|---|---|---|
| 1 | Channels (LIVE) | NOT REQUIRED / REQUIRED | |
| 2 | Movies (VOD) | NOT REQUIRED / REQUIRED | |
| 3 | Series (VOD) | NOT REQUIRED / REQUIRED | |
| 4 | SVOD | NOT REQUIRED / REQUIRED | |
| 5 | TVOD / PPV | NOT REQUIRED / REQUIRED | |
| 6 | AVOD / FAST | NOT REQUIRED / REQUIRED | |
| 7 | Widevine DRM | NOT REQUIRED / REQUIRED | |
| 8 | FairPlay DRM | NOT REQUIRED / REQUIRED | |
| 9 | PlayReady DRM | NOT REQUIRED / REQUIRED | |
| 10 | CSAI | NOT REQUIRED / REQUIRED | |
| 11 | SSAI | NOT REQUIRED / REQUIRED | |
| 12 | Geo-blocking | NOT REQUIRED / REQUIRED | |

---

## Integrations Table

| # | Component | Required? | Comments |
|---|---|---|---|
| 1 | Localization Service | NOT REQUIRED / KEEP / REPLACE | |
| 2 | Consent Management Platform | NOT REQUIRED / KEEP / REPLACE | |
| 3 | Media Asset Manager | NOT REQUIRED / KEEP / REPLACE | |
| 4 | Content Management System | NOT REQUIRED / KEEP / REPLACE | |
| 5 | Ad Server (AVOD) | NOT REQUIRED / KEEP / REPLACE | |
| 6 | Payment Gateways (SVOD/TVOD) | NOT REQUIRED / KEEP / REPLACE | |
| 7 | User Identity Management | NOT REQUIRED / KEEP / REPLACE | |
| 8 | CRM / Customer Support System | NOT REQUIRED / KEEP / REPLACE | |
| 9 | Usage & Playback Analytics | NOT REQUIRED / KEEP / REPLACE | |
| 10 | Video Player | NOT REQUIRED / KEEP / REPLACE | |
| 11 | CDN | NOT REQUIRED / KEEP / REPLACE | |

---

## Output

- Save to `output-files/discovery-sessions/YYYY-MM-DD_discovery-[prospect-slug].md`
- Ask: "Would you like me to create this Discovery Template directly in Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`
