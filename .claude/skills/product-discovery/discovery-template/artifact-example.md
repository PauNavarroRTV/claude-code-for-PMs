# Artifact Example — Discovery Template

> Reference only. Shows structure and quality bar.
> Source: kb/discovery-template.md

---

# Discovery Template — YYYY.MM.DD [Prospect Name]

## Header

| Field | Value |
|---|---|
| Discovery Status | DRAFT |
| Discovery Date | 2026-07-01 |
| Discovery Owner | @Pau Navarro |
| Discovery Participants | [Name / Role] |
| Prospect Name | [Prospect name] |
| Prospect Website | [URL] |
| Prospect Platform | [Reference OTT platform if any] |

## Summary

A European broadcaster seeking to launch a white-label OTT app covering CTV (Samsung, LG) and mobile (iOS, Android). Primary monetisation: AVOD + FAST. No existing streaming infrastructure — full greenfield deployment.

- **Device Coverage:** Samsung, LG, iOS, Android required. Roku and Web TBC.
- **Branding:** Config-driven. Full white-label. Custom fonts and splash screen required.
- **Monetisation:** AVOD + FAST channels. SVOD potential in phase 2. SSAI required.
- **Authentication:** Email/Password + optional SSO. Gated playback for premium content. Profiles required.
- **Integrations:** Replacing CMS with RTV MAM. Keeping existing analytics (NPAW). New ad server (SpringServe).

## Platform Device Coverage

| # | Device Type | Device OS | Required? | Comments |
|---|---|---|---|---|
| 1 | Smart TV | Tizen OS (Samsung) | REQUIRED | |
| 2 | Smart TV | LG webOS | REQUIRED | |
| 3 | Smart TV | Android TV | NOT REQUIRED | Phase 2 |
| 4 | Mobile | Android | REQUIRED | |
| 5 | Mobile | iOS | REQUIRED | |
| 6 | Web | Chrome/Safari | NOT REQUIRED | TBC |
| 7 | Streaming Stick | Roku | NOT REQUIRED | TBC |

## Platform Branding & Localization

| # | Item | Required? | Comments |
|---|---|---|---|
| 1 | Config-driven branding | CONFIG-DRIVEN | |
| 2 | Logo | REQUIRED | |
| 3 | Color Palette | REQUIRED | |
| 4 | Custom Fonts | REQUIRED | |
| 5 | Custom Splash Screen | REQUIRED | |
| 6 | Languages | REQUIRED | EN, ES, FR |
| 7 | RTL Languages | NOT REQUIRED | |

## Platform Content Monetization

| # | Item | Required? | Comments |
|---|---|---|---|
| 1 | Channels (LIVE) | REQUIRED | FAST channels |
| 2 | Movies (VOD) | REQUIRED | AVOD |
| 3 | Series (VOD) | REQUIRED | AVOD |
| 4 | AVOD/FAST | REQUIRED | Primary model |
| 5 | SVOD | NOT REQUIRED | Phase 2 |
| 6 | TVOD/PPV | NOT REQUIRED | |
| 7 | Widevine DRM | REQUIRED | |
| 8 | FairPlay DRM | REQUIRED | iOS |
| 9 | SSAI | REQUIRED | SpringServe + MediaTailor |
| 10 | Geo-blocking | REQUIRED | EU rights |

## Platform User Authentication

| # | Item | Required? | Comments |
|---|---|---|---|
| 1 | Email/Password Login | REQUIRED | |
| 2 | Social Login | NOT REQUIRED | |
| 3 | Anonymous Playback | REQUIRED | FAST channels |
| 4 | Gated Playback | REQUIRED | Premium AVOD |
| 5 | Multiprofile | REQUIRED | |
| 6 | Continue Watching | REQUIRED | |

## Integration with Platform Core Components

| # | Component | Required? | Comments |
|---|---|---|---|
| 1 | Media Asset Manager | REPLACE | Moving to RTV MAM |
| 2 | Ad Server (AVOD) | REPLACE | SpringServe |
| 3 | Usage & Playback Analytics | KEEP | NPAW retained |
| 4 | CDN | KEEP | Existing CDN |
| 5 | User Identity Management | REPLACE | Firebase |
