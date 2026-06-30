# Artifact Example — Functional Definition

> Reference only. Shows structure and quality bar. Do not copy content verbatim.
> Source: kb/example-functional-definition.md

---

# [FD] 2026Q1 [CTV] VOD Detail Pages

## Header

| Field | Value |
|---|---|
| Target Release | Mar 5, 2026 |
| Target Devices | CTV |
| Jira Epic | [Epic link] |
| Signature | SIGNED OFF |
| Dev Readiness | PRODUCT-READY / DESIGN-READY |
| Product | @Pau Navarro |
| Designer | @Leandro de Medeiros Corrêa |
| Developer | @Sergio Revueltas |
| QA | @Pedro Martin |

## Summary

This FD outlines the VOD content detail page for CTV devices, emphasizing a consistent layout. It details display of MAM-sourced metadata including clickable elements (genres, director, cast), along with 16:9 artwork. Prominent action buttons for Watch and Trailer playback are included. Skeleton states ensure layout stability during loading.

## Acceptance Criteria

**Content Detail Page Display**
```
GIVEN a user selects a VOD item from a content list
  WHEN navigation to the content detail page completes
  THEN a dedicated VOD content detail page is displayed
  AND the page includes metadata, artwork, CTA buttons, and clickable elements
```

**Metadata Rendering**
```
GIVEN the VOD content detail page is displayed
  WHEN the page loads
  THEN display from MAM: Cover (16:9), Title, Age Rating, Genres (first two only), Release Year, Short Description
  AND display actionable elements: Watch, Trailer (if available), clickable Cast/Genres/Episodes
  AND leave blank any unavailable metadata fields — do not display placeholder text
```

**CTA Buttons**
```
GIVEN the VOD content detail page is displayed
  WHEN user actions are available
  THEN display: Watch (triggers playback from beginning), Trailer (triggers trailer without affecting main content progress)
  AND Trailer button appears only if corresponding content exists
```

## DON'Ts

**Layout**
- Do NOT introduce multiple layout variants for VOD detail pages
- Do NOT display placeholder text for missing metadata
- Do NOT alter the column structure (Left/Right) on filtered or More Info pages

**Actions & Playback**
- Do NOT start main content playback automatically when detail page loads
- Do NOT start full content playback when selecting Trailer action

## User Interactions & Designs

**Detail Page Layout:**
1. **Header / Top Section** — Title Treatment, Release Year, Age Rating, Genres, Duration, Short Description (max 300 chars), 16:9 artwork
2. **User Action Buttons** — Watch (primary focus), Trailer
3. **Clickable Elements** — Genres, Cast, Director; clicking navigates to filtered content page
4. **More Details** — navigates to full metadata page

**Skeleton Behavior:**
- Skeleton appears immediately after user clicks content item
- Skeleton-Contextual-Information + Skeleton-Button-List
- Both elements are non-interactive placeholders
- Replaced by actual content once page fully loads

## Success Metrics

| Metric | Description | Target Value |
|---|---|---|
| Detail page load time | Time from click to fully rendered page | < 2s |
| CTA click-through rate | % of users who click Watch after visiting detail page | > 60% |
