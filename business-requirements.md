# BoligPass — Business Requirements

## 1) Problem, users, outcomes
- Problem: Home data is scattered and static. Buyers and owners face hidden costs, decision overload, and slow, manual processes. :contentReference[oaicite:0]{index=0}
- Primary users: First-time buyers and young families (“Rising Young”) and Upper Affluent owners. :contentReference[oaicite:1]{index=1}
- Outcomes
  - Buyers: Clear first-year plan, price-negotiation leverage, cost visibility. :contentReference[oaicite:2]{index=2}
  - Owners: Living “home passport” with receipts, warranties, maintenance, nudges. :contentReference[oaicite:3]{index=3}
  - Sellers: Exportable, trustworthy seller pack. :contentReference[oaicite:4]{index=4}
  - Bank/Insurance: Better pre-approval, lower churn, risk/claim reduction. :contentReference[oaicite:5]{index=5} :contentReference[oaicite:6]{index=6}

## 2) Value prop
“Dynamic Home Service Book” that turns public data, inspection reports, and receipts into a living passport. Day-one value before purchase; compounding value after move-in; proof at sale. :contentReference[oaicite:7]{index=7}

## 3) Core jobs-to-be-done (JTBD) and top features (MVP)
- JTBD: Decide fast and fairly when buying; prevent avoidable failures; prove home care at sale. :contentReference[oaicite:8]{index=8}
- MVP features (release 1)
  1) **Pre-Buy Report** from address + reports: top risks, cost bands, negotiation checklist. :contentReference[oaicite:9]{index=9}
  2) **Auto-Passport**: email-forward receipts; parse warranties; link manuals. :contentReference[oaicite:10]{index=10}
  3) **Lifecycle & Maintenance**: asset lifespans, tasks, smart reminders, seasonal nudges. :contentReference[oaicite:11]{index=11}
  4) **Milestone Plan** for small renovations with suggested sequencing. :contentReference[oaicite:12]{index=12}
  5) **Seller Export** with evidence trail and improvements. :contentReference[oaicite:13]{index=13}

## 4) Data sources and ingestion
- Public: BBR, Energimærke/EPC, Tilstandsrapport, geo-signals (e.g., flood/radon). :contentReference[oaicite:14]{index=14}
- Private: Receipts via email-forwarding; contractor uploads with photos and sign-offs. :contentReference[oaicite:15]{index=15}
- Bank/insurance hooks: Only as explicit, revocable connections aligned with DB housing flows. :contentReference[oaicite:16]{index=16}

## 5) Must-have quality bars (bank-grade UX)
- Clear, calm, low-risk UI; high legibility; predictable flows; evidence over claims. :contentReference[oaicite:17]{index=17} :contentReference[oaicite:18]{index=18}
- Fast first value: address → instant draft report in <1 minute (target). :contentReference[oaicite:19]{index=19}
- Exportable, verifiable PDFs for buyer/seller/insurer. :contentReference[oaicite:20]{index=20}

## 6) Acceptance criteria (MVP)
- Address + at least one report produces a Pre-Buy Report with: top 5 risks, 3 cost bands, 10 negotiation checks. :contentReference[oaicite:21]{index=21}
- Email-forwarded receipt creates an item with: vendor, item, serial/model, date, warranty end, file+URL, and manual link if found.
- Maintenance schedule auto-populates ≥10 baseline tasks by season and asset age; user can snooze/complete.
- Seller Export compiles: documents list, upgrades log, photos, timestamps, contractor evidence.
- PII stored in EU region; all actions auditable.

## 7) Out-of-scope for MVP
- Deep climate-adaptation advisory; show basic geo-signals only. :contentReference[oaicite:22]{index=22}
- Full contractor marketplace; allow private contractor uploads only. :contentReference[oaicite:23]{index=23}

## 8) Regulatory, risk, and partner fit
- Aligns with Forward ’28 digital-first housing experience, proactive nudges, and modular add-ons. :contentReference[oaicite:24]{index=24} :contentReference[oaicite:25]{index=25}
- Supports DB housing positioning and Rising Young track. :contentReference[oaicite:26]{index=26} :contentReference[oaicite:27]{index=27}
- Churn levers: better advice, faster processing, clearer pricing signals. :contentReference[oaicite:28]{index=28}

## 9) Success metrics (first 90 days)
- Activation: ≥40% of new users reach a generated Pre-Buy Report.
- Retention: Day-30 ≥25% with ≥3 passport items or 1 completed task.
- Proof usage: ≥20% export Seller Pack or share a passport view.
- Partner impact: measurable increase in qualified housing leads and reduced advisory time. :contentReference[oaicite:29]{index=29}

## 10) Competitive anchor
- Differentiate vs. insurer apps and vaults by day-one buying value + evidence-grade seller export. :contentReference[oaicite:30]{index=30}
