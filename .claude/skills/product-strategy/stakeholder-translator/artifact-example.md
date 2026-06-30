# Artifact Example — Stakeholder Translator

> Reference only. Shows the three-voice format for the same update.

---

## Input

> "We're adding an ad countdown timer to FAST live channels on CTV. The timer will show how many seconds remain in the current ad break. It appears as an overlay in the bottom-right corner of the screen during ad pods."

---

## Voice 1 — Technical (Engineering)

```
🔧 Technical Update — FAST Ad Countdown Timer (CTV)

What changed:
Ad pod overlay now displays a countdown timer showing seconds remaining in the current break. Timer appears in bottom-right corner, visible for the duration of the ad pod.

Affected surfaces:
CTV only (React codebase). Not scoped for Mobile or Web in this iteration.

Technical notes:
- Timer reads break duration from #EXT-X-CUE-OUT tag in HLS playlist
- Overlay must not interfere with ad creative safe zones
- Timer starts at break duration and counts down to 0
- On pod end (#EXT-X-CUE-IN), overlay dismisses automatically
- SSAI architecture: AWS MediaTailor provides break duration metadata

Open questions:
- Does the timer reset per individual ad or per full pod?
- What is the fallback when break duration metadata is unavailable?
```

---

## Voice 2 — Outcome-Focused (Execs)

```
📊 Exec Update — FAST Ad Countdown Timer (CTV)

What we're doing:
Adding visible ad break duration to FAST live channels, reducing viewer drop-off during ad pods.

Why it matters:
Ad pod abandonment is the primary churn trigger for FAST viewers. Showing the countdown sets expectations and retains attention — directly impacting ad impressions delivered per session.

Expected impact:
Industry benchmarks show 10–15% reduction in ad break abandonment with countdown UI. For AVOD partners, this is a direct revenue retention lever.

Timeline:
Q3 2026 (CTV)

Risk:
Timer accuracy depends on SSAI metadata quality — partner ad server configuration gaps could cause incorrect countdown display.
```

---

## Voice 3 — Plain Language (Partners / Users)

```
📢 Partner Update — FAST Ad Countdown Timer (CTV)

What's new:
Your viewers will now see a small timer on screen showing how many seconds are left in each ad break on your FAST channels.

What this means for you:
Viewers are less likely to switch channels during ads when they can see the break is almost over. More viewers staying through the break means more completed ad impressions — better results for your advertisers.

When:
Coming in Q3 2026 on CTV apps.

Anything you need to do:
Nothing — this is applied automatically to all FAST channels. No configuration required.
```
