# Design System — BoligPass

## Principles
- Bank-grade calm. Minimal, legible, predictable.
- Show evidence. Reduce cognitive load. No dark patterns. :contentReference[oaicite:35]{index=35} :contentReference[oaicite:36]{index=36}

## Typography
- **Inter** as primary family.
- Type scale: 12, 14, 16, 20, 24, 32, 40.
- Line heights generous; numbers tabular where applicable.

## Color
- Primary **Blue** palette for trust; neutral grays for structure.
  - `primary-900` #0A2A4A
  - `primary-700` #104C86
  - `primary-600` #1363B3
  - `primary-500` #1773D1
  - `primary-100` #E6F0FB
  - `success` #1F8A4D
  - `warning` #B7791F
  - `danger`  #B91C1C
- Usage: limited accents, high contrast, WCAG AA minimum.

## Layout & spacing
- Grid with 8px spacing. Max content width 1024–1200px.
- Cards with 8–16px padding, 6–8px radius, subtle shadows only.

## Components (shadcn + MagicUI)
- **AppFrame**: shell with top nav and context panel.
- **ReportCard**: risk/cost band, evidence count, last updated.
- **TaskList**: grouped by due date; quick “snooze/complete.”
- **AssetPanel**: lifespan, warranty, receipts, manuals.
- **ExportDrawer**: select sections → generate PDF.
- **ConsentBanner**: granular toggles for data sharing.

## States & feedback
- “Confidence” badge on parsed fields.
- Timeline events for all writes and imports.
- Clear error recovery for parsing/ingestion.

## Motion
- Subtle only. 150–200ms. No distracting parallax. Matches “bank look.” :contentReference[oaicite:37]{index=37}

## Content style
- Short, declarative copy. Avoid jargon. Explain terms inline during housing journeys. :contentReference[oaicite:38]{index=38}

## Screens to prioritize
1) **Pre-Buy Report**: address header, risks, cost bands, negotiation checklist. :contentReference[oaicite:39]{index=39}
2) **Passport Home**: tasks, assets, receipts, warranties. :contentReference[oaicite:40]{index=40}
3) **Seller Export**: sections, preview, share/download. :contentReference[oaicite:41]{index=41}
4) **Onboarding (Rising Young)**: warm guidance and quick value. :contentReference[oaicite:42]{index=42}

## Brand alignment
- Align with DB housing positioning and proof points without copying brand assets; emphasize clarity, advice, and whole-journey support. :contentReference[oaicite:43]{index=43}
