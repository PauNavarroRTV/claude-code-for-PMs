# Tech Stack

> Pau-authored. Agent reads, never modifies.
> Source: kb/frontend-tech-stack.md — Version 1.3, April 2026

---

## Architecture Overview

**Hybrid-Native model:** The majority of development effort is concentrated in high-reuse layers (React for CTV/Web, KMP for Mobile), while platform-mandated native builds (tvOS, Roku) are maintained by specialist teams as strategic necessities.

```
┌───────────────────────────────────────────────────────────────────────┐
│              WHITE LABEL OTT APPS — UNIFIED PLATFORM                │
├───────────────────────────────────────────────────────────────────────┤
│  FRONT-END LAYER                                                     │
│  CTV (Smart TV, STB, Roku, Console, Apple TV)                       │
│  Web                                                                 │
│  Mobile (iOS & Android)                                              │
│  Built with: React (CTV/Web) | KMP (Mobile) |                       │
│              BrightScript (Roku) | Swift/SwiftUI (tvOS)             │
├───────────────────────────────────────────────────────────────────────┤
│  MONETISATION LAYER                                                  │
│  AVOD | FAST | TVOD | SVOD | Hybrid | SSAI | Entitlement            │
├───────────────────────────────────────────────────────────────────────┤
│  INTEGRATION LAYER                                                   │
│  CMS/MAM | Ad Tech | Analytics | CDN | Payments | CRM               │
│  Backend-agnostic | No vendor lock-in | API-first                   │
├───────────────────────────────────────────────────────────────────────┤
│  FOUNDATION LAYER                                                    │
│  DRM | Geo-blocking | Consent Management | App Store Release Mgmt   │
│  Privacy-first Analytics | Operational Support Model                │
└───────────────────────────────────────────────────────────────────────┘
```

---

## Stack Summary by Device Family

| Device Family | Language | UI Framework | Code Sharing |
|---|---|---|---|
| CTV + Web | TypeScript / JavaScript | React + Vanilla Extract | Unified codebase across all modern web-runtime surfaces |
| Mobile iOS | Swift | SwiftUI | Shared business logic via KMP |
| Mobile Android | Kotlin | Jetpack Compose | Shared business logic via KMP |
| Roku | BrightScript | SceneGraph XML | None — dedicated platform |
| tvOS | Swift | SwiftUI (+ UIKit) | Partial overlap with iOS Swift |
| Automotive IVI | TypeScript / JavaScript | React + Adaptation Layer | High — extends CTV/Web base |
| HbbTV | TypeScript / JavaScript | React + HbbTV Adaptation Layer | High — extends CTV/Web base |

---

## CTV + Web — React

A single, unified React codebase serves all CTV and web surfaces.

**Supported devices:**
- Samsung Tizen (2018+)
- LG webOS (2018+)
- Hisense (2020+)
- Android TV, Sony, Panasonic, Vestel, Philips, TCL
- Web: Chrome, Firefox, Safari, Edge
- Consoles: PlayStation 5
- STBs: Android-based, Netgem

**Styling architecture:** Vanilla Extract — generates all CSS at build time (static stylesheets). Deliberately replaces styled-components (runtime CSS) used in legacy Rakuten TV UI40. Benefits: reduced JS bundle size, faster FCP/LCP, minimised main thread blocking, type safety.

**Legacy device note:** Hisense 2019 and earlier, LG 2017 and earlier, Samsung 2017 and earlier, PS4 not supported — require CSS Variables which are a Vanilla Extract requirement. Affected devices: ~1.9% of plays, 1.6% unique viewers, 2.2% ad impressions, 3.7% revenue on the Rakuten TV CTV base.

---

## Mobile — Kotlin Multiplatform (KMP)

Core business logic written once, shared across iOS and Android. UI layer is platform-native.

**Shared via KMP:**
- Playback state management
- Content catalogue & metadata fetching
- User authentication & session handling
- Analytics event tracking
- Download & offline playback logic
- Monetisation logic (AVOD / SVOD / TVOD)

**Native UI:** SwiftUI on iOS, Jetpack Compose on Android.

---

## Roku — BrightScript

Roku mandates BrightScript + SceneGraph XML. No code sharing with other platforms. Dedicated Roku engineers. Key market: #1 streaming platform in the US.

---

## tvOS — Swift / SwiftUI

Apple mandates Swift/SwiftUI for tvOS. No code sharing with other CTV platforms. Partial overlap with iOS Swift. Dedicated tvOS engineers. Distribution via Apple TV App Store.

---

## Automotive IVI — React + Adaptation Layer

Extends CTV/Web React codebase. Deployed on LG webOS Automotive. Proven OEMs: Kia, Hyundai (LG-based IVI).

**Adaptation Layer handles:**
- Steering wheel and hardware button inputs
- Touch and hybrid interaction models
- Focus engine tuning for in-car usability
- Layout adjustments for dashboard aspect ratios

---

## HbbTV — React + HbbTV Adaptation Layer

Extends CTV/Web React codebase. Standard: HbbTV 2.0.4. Distribution: broadcast AIT signal — no app store. Key markets: Europe (UK, DE, FR, ES, IT).

**Adaptation Layer handles:**
- AIT-triggered app lifecycle events
- D-pad remote control navigation
- DVB-DASH live channel manifest handling
- GDPR-compliant CMP flow within HbbTV runtime

**Streaming:** MPEG-DASH / DVB-DASH (live), HLS (VOD) | **DRM:** PlayReady (primary)

---

## Video Playback Layer

### Player Technology by Platform

| Platform | Player Engine | Formats | DRM |
|---|---|---|---|
| CTV + Web (Smart TVs, STBs, Consoles, Web) | HTML5 / Shaka Player | HLS, MPEG-DASH | Widevine, PlayReady |
| Android / Android TV | ExoPlayer / Media3 | HLS, MPEG-DASH | Widevine |
| iOS | AVPlayer | HLS | FairPlay |
| tvOS | AVPlayer | HLS | FairPlay |
| Roku | Native SceneGraph Player | HLS, MPEG-DASH | Widevine |
| HbbTV | Shaka Player (HTML5) | MPEG-DASH, DVB-DASH, HLS | PlayReady |

**Player Abstraction:** Mystique Interface — Rakuten TV's unified player interface that abstracts device-specific player implementations behind a single API surface.

### iOS Playback
AVPlayer for all content types (live, AVOD, SVOD, TVOD). HLS + FairPlay across the board. Full HD and 4K available for all content.

### HLS Live Channel Quality Tiers

| Tier | Resolution | Approx. Bandwidth |
|---|---|---|
| 0 | 448×252 | ~583 Kbps |
| 1 | 768×432 | ~980 Kbps |
| 2 | 768×432 | ~1.58 Mbps |
| 3 | 1280×720 | ~2.83 Mbps |
| 4 | 1920×1080 | ~4.95 Mbps |

### SSAI Architecture for Live Channels
AWS MediaTailor + Springserve. Three components: Sherlock (via CDN) → Springserve (ad decision) → AWS MediaTailor (ad replacement).

---

## Streaming Formats

| Format | Extension | Use Case |
|---|---|---|
| HLS | .m3u8 | VOD + Live — primary format for all Apple surfaces |
| MPEG-DASH | .mpd | VOD + Live — preferred for Widevine and PlayReady DRM |
| LL-HLS | .m3u8 | Low-latency live streaming — live sports, news |
| CMAF | .m4s | Unified delivery — single encrypted stream for HLS and DASH clients |

---

## Encoding Profiles

| Profile | Max Resolution | Video Codec | HDR | Audio |
|---|---|---|---|---|
| SD | 960×540 | H.264 | SDR | AAC / EAC3 / Dolby Atmos |
| HD | 1280×720 | H.264 | SDR | AAC / EAC3 / Dolby Atmos |
| FHD | 1920×1080 | H.264 | SDR | AAC / EAC3 / Dolby Atmos |
| UHD SDR | 3840×2160 | H.265 | SDR | AAC / EAC3 / Dolby Atmos |
| UHD HDR10 | 3840×2160 | H.265 | HDR10 | AAC / EAC3 / Dolby Atmos |
| UHD HDR10+ | 3840×2160 | H.265 | HDR10+ | AAC / EAC3 / Dolby Atmos |
| UHD IMAX Enhanced | 3840×2160 | H.265 | IMAX Enhanced | AAC / EAC3 / DTS:X / Dolby Atmos |
| UHD Dolby Vision | 3840×2160 | dvhe / Jpeg2000 | Dolby Vision | AAC / EAC3 / Dolby Atmos |

All profiles include full ABR ladder from 448×252 at ~350 Kbps. Frame rate: 25 fps. Audio: 48 kHz.

---

## DRM Support

| DRM System | Platforms |
|---|---|
| Widevine | CTV (Smart TVs, STBs, Consoles), Web, Android, Android TV, Roku |
| FairPlay | iOS (all content types), tvOS |
| PlayReady | CTV — Microsoft Edge, Windows, Xbox, HbbTV |

### DRM Security Level by Quality Tier

| Quality | DRM Requirement | HDCP |
|---|---|---|
| SD | Widevine L3 / PlayReady SL2000 | HDCP 1.0 |
| HD | Widevine L3 / PlayReady SL2000 | HDCP 2.1 |
| FHD | Widevine L3 / PlayReady SL2000 (Disney: SL3000 or Widevine L1 required) | HDCP 2.1 |
| UHD | PlayReady SL3000 (some studios permit Widevine L1) | HDCP 2.2 |

### Key Studio-Specific Constraints

| Studio | Notable Requirement |
|---|---|
| Paramount, Universal, Warner Bros. | Separate unique encryption keys for SD, HD, and UHD streams |
| Disney | Max 2 concurrent streams (TVOD); 30-day + 48h playback window; no UHD downloads; HDCP 2.2 for FHD/UHD |
| Sony | Max 5 devices, 2 concurrent streams; HDCP 2.2 for UHD |
| Universal | Encryption key rotation minimum every 5 minutes |

### Additional Content Protection

| Capability | Detail |
|---|---|
| Geo-filtering | IP geolocation + VPN detection via MaxMind GeoIP2 |
| Device limits | Maximum 5 registered devices per account |
| Root/jailbreak detection | Enforced on Android and Apple devices |
| App obfuscation | Required by Warner Bros.; implemented at build level |
| Concurrent stream enforcement | Configurable per studio/content type |
