# Tech Stack and Architecture

## Frontend
- **Next.js (App Router)** for SSR/SSG, route handlers, and edge streaming.
- **UI**: shadcn/ui + **MagicUI** components on top of **Tailwind**.
- **State**: Server Components + React Query where needed.
- **Forms**: React Hook Form + Zod.
- **i18n**: next-intl.

## Backend
- **Supabase** (Postgres, Auth, Storage, Edge Functions, Realtime).
- **APIs**
  - Ingestion endpoints: address lookup, report upload, email-forward parser, contractor evidence.
  - Report builder service: composes Pre-Buy Report from public + uploaded data.
  - Exporter service: compiles “Seller Pack” PDF.
- **Jobs**
  - Receipt OCR + warranty extraction (Edge Function + OCR library).
  - Manual fetchers for manuals (safe allowlist domains).
  - Reminder scheduler (cron) writing tasks to user timelines.

## Data model (initial)
- `users` (supabase auth uid, role, consent flags)
- `homes` (address, geo_hash, epc_grade, year_built, meta)
- `reports` (type: tilstandsrapport/epc/bbr/custom, source, parsed_json, files[])
- `assets` (home_id, kind, make_model, serial, installed_at, lifespan_months)
- `receipts` (asset_id?, vendor, amount, purchase_date, warranty_end, file)
- `tasks` (home_id, type: maintenance/permit/warranty, due_at, status)
- `evidence` (task_id|asset_id, photos[], contractor_id, signoff, checksum)
- `exports` (home_id, type: seller_pack, file_url, created_at)
- `integrations` (bank/insurer flags, tokens if any, scope, expires_at)

## Security & compliance
- Supabase EU region. Row Level Security on all tables. Signed URLs for files.
- Field-level encryption for sensitive docs; hashed file checksums in `evidence`.
- Full audit log of data mutations and export events.
- Principle of least privilege for service keys.

## Observability
- Edge Function logs + Postgres logs.
- App metrics: activation funnels, task completion, export events.

## Delivery
- CI: typecheck, lint, test, DB migrations, preview deploy.
- Hosting: Vercel for web; Supabase managed for DB/functions.

## Bank/insurance alignment
- Digital front door, proactive nudges, and exportable evidence align with DB housing journey and GTM housing positioning. :contentReference[oaicite:31]{index=31} :contentReference[oaicite:32]{index=32}

## Risks & mitigations
- **Parsing quality** → human-readable “Confidence” flags; allow user corrections.
- **Data rights** → explicit per-home consent; granular scopes for partners. :contentReference[oaicite:33]{index=33}
- **Churn sensitivity** → transparent cost bands and clear advice surfaces. :contentReference[oaicite:34]{index=34}
