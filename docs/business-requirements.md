# BoligPass — Business Requirements

## 1) Problem, users, outcomes
- Problem: Home data is scattered and static. Buyers and owners face hidden costs, decision overload, and slow, manual processes.
- Primary users: First-time buyers and young families ("Rising Young") and Upper Affluent owners.
- Outcomes
  - Buyers: Clear first-year plan, price-negotiation leverage, cost visibility.
  - Owners: Living "home passport" with receipts, warranties, maintenance, nudges.
  - Sellers: Exportable, trustworthy seller pack.
  - Bank/Insurance: Better pre-approval, lower churn, risk/claim reduction.

## 2) Value prop
"Dynamic Home Service Book" that turns public data, inspection reports, and receipts into a living passport. Day-one value before purchase; compounding value after move-in; proof at sale.

## 3) Core jobs-to-be-done (JTBD) and top features (MVP)
- JTBD: Decide fast and fairly when buying; prevent avoidable failures; prove home care at sale.
- MVP features (release 1)
  1) **Pre-Buy Report** from address + reports: top risks, cost bands, negotiation checklist.
  2) **Auto-Passport**: email-forward receipts; parse warranties; link manuals.
  3) **Lifecycle & Maintenance**: asset lifespans, tasks, smart reminders, seasonal nudges.
  4) **Milestone Plan** for small renovations with suggested sequencing.
  5) **Seller Export** with evidence trail and improvements.

## 4) Data sources and ingestion
- Public: BBR, Energimærke/EPC, Tilstandsrapport, geo-signals (e.g., flood/radon).
- Private: Receipts via email-forwarding; contractor uploads with photos and sign-offs.
- Bank/insurance hooks: Only as explicit, revocable connections aligned with DB housing flows.

## 5) Must-have quality bars (bank-grade UX)
- Clear, calm, low-risk UI; high legibility; predictable flows; evidence over claims.
- Fast first value: address → instant draft report in <1 minute (target).
- Exportable, verifiable PDFs for buyer/seller/insurer.

## 6) Acceptance criteria (MVP)
- Address + at least one report produces a Pre-Buy Report with: top 5 risks, 3 cost bands, 10 negotiation checks.
- Email-forwarded receipt creates an item with: vendor, item, serial/model, date, warranty end, file+URL, and manual link if found.
- Maintenance schedule auto-populates ≥10 baseline tasks by season and asset age; user can snooze/complete.
- Seller Export compiles: documents list, upgrades log, photos, timestamps, contractor evidence.
- PII stored in EU region; all actions auditable.

## 7) Out-of-scope for MVP
- Deep climate-adaptation advisory; show basic geo-signals only.
- Full contractor marketplace; allow private contractor uploads only.

## 8) Regulatory, risk, and partner fit
- Aligns with Forward '28 digital-first housing experience, proactive nudges, and modular add-ons.
- Supports DB housing positioning and Rising Young track.
- Churn levers: better advice, faster processing, clearer pricing signals.

## 9) Success metrics (first 90 days)
- Activation: ≥40% of new users reach a generated Pre-Buy Report.
- Retention: Day-30 ≥25% with ≥3 passport items or 1 completed task.
- Proof usage: ≥20% export Seller Pack or share a passport view.
- Partner impact: measurable increase in qualified housing leads and reduced advisory time.

## 10) Competitive anchor
- Differentiate vs. insurer apps and vaults by day-one buying value + evidence-grade seller export.
