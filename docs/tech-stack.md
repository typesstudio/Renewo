# Tech Stack and Architecture

## Core Decisions
- **Simplicity First**: Plain Postgres over Supabase (no realtime needs)
- **Cost Effective**: NextAuth over Clerk, R2 over S3
- **Type Safety**: TypeScript strict + Prisma ORM
- **EU Compliance**: All data hosted in EU regions
- **Progressive Enhancement**: Start with sync APIs, add jobs when needed

## Development Environment
- **Runtime**: Node 24.x pinned via Volta
- **Package Manager**: PNPM via Corepack
- **TypeScript**: Strict mode enabled
- **Environment**: direnv + 1Password for secrets management
- **Env Validation**: @t3-oss/env-nextjs with Zod schemas

## Frontend
- **Framework**: Next.js 14+ (App Router) for SSR/SSG, route handlers, and edge streaming
- **UI**: shadcn/ui + **MagicUI** components on top of **Tailwind CSS**
- **State**: Server Components by default + React Query for client-side data fetching
- **Forms**: React Hook Form + Zod validation
- **i18n**: next-intl for internationalization

## Code Quality & Testing
- **Linting**: ESLint with next/core-web-vitals preset
- **Formatting**: Prettier with Tailwind plugin
- **Type Checking**: TypeScript strict mode
- **Unit Testing**: Vitest + React Testing Library
- **E2E Testing**: Playwright (when needed)
- **API Mocking**: MSW for development and testing
- **Git Hooks**: simple-git-hooks + lint-staged for pre-commit checks

## Backend
- **Database**: PostgreSQL on Render with Prisma ORM
- **Authentication**: NextAuth (Auth.js) for user management
  - Email/password and OAuth providers (Google, Apple)
  - Session management in database
  - Custom user properties for multi-home access
- **File Storage**: Cloudflare R2 for receipts, PDFs, photos
  - Cost-effective S3-compatible API
  - EU bucket for GDPR compliance
- **APIs** (Next.js Route Handlers):
  - Ingestion endpoints: address lookup, report upload, email parser, contractor evidence
  - Report builder service: composes Pre-Buy Report from data
  - PDF exporter: generates "Seller Pack" documents
- **Background Jobs** (add later if needed):
  - Initially: Synchronous processing in API routes
  - Future: Inngest or Trigger.dev for long-running tasks
- **External Services**:
  - OCR: Google Cloud Vision API (pay-per-use)
  - PDF Generation: React PDF (serverless-friendly)

## Data model (initial)
- `users` (id, email, name, image, emailVerified) - NextAuth schema
- `accounts` (userId, provider, providerAccountId) - OAuth connections
- `sessions` (userId, sessionToken, expires) - Active sessions
- `homes` (id, address, geo_hash, epc_grade, year_built, metadata)
- `user_homes` (user_id, home_id, role: owner/manager/viewer, invited_by)
- `reports` (home_id, type: tilstandsrapport/epc/bbr, source, parsed_json, file_urls[])
- `assets` (home_id, category, make_model, serial_number, installed_date, lifespan_months)
- `receipts` (asset_id?, vendor, amount, purchase_date, warranty_expiry, file_url)
- `tasks` (home_id, type: maintenance/permit/warranty, due_date, status, completed_at)
- `evidence` (task_id|asset_id, photo_urls[], contractor_id, signoff_date, checksum)
- `exports` (home_id, type: seller_pack, file_url, created_at, expires_at)
- `integrations` (user_id, provider, scopes, encrypted_tokens, expires_at)

## Security & compliance
- **Database**: EU-hosted Postgres (GDPR compliance)
- **Access Control**: Role-based permissions via application layer
- **File Security**: Signed URLs with expiration for all file access
- **Encryption**: Field-level encryption for sensitive documents
- **Integrity**: SHA-256 checksums for evidence/document verification
- **Audit Trail**: Comprehensive logging of all data mutations and exports
- **API Security**: Rate limiting, API keys for external integrations
- **Secrets Management**: Environment variables via 1Password/Vercel

## Observability
- **Logging**: Structured logs via Pino or Winston
- **Error Tracking**: Sentry for production error monitoring
- **Database Monitoring**: Query performance via Postgres insights
- **Application Metrics**:
  - User activation funnels
  - Task completion rates
  - Export generation events
  - API response times
- **Uptime Monitoring**: BetterStack or Checkly

## CI/CD & Deployment
- **CI Pipeline**: GitHub Actions
  - Typecheck, lint, test on every PR
  - Database migrations via Prisma Migrate
  - Preview deploys for PRs
- **Dependency Management**: Renovate for automated updates
- **Hosting**:
  - Web & API: Render (configured via render.yaml)
  - Database: Render PostgreSQL (Frankfurt region for EU compliance)
  - File Storage: Cloudflare R2 (EU bucket)
  - Background Jobs: Inngest (when needed)
- **Environment Management**:
  - Staging: Auto-deploy from main branch
  - Production: Manual promotion with migration checks
  - Secrets: Render environment groups + 1Password

## Project Structure
- **Monolithic Start**: Single Next.js app (add Turborepo later if needed)
- **Source Organization**: `/src` directory with App Router structure
- **Configuration Files**:
  - `.npmrc`, `.editorconfig`, `.gitattributes` for consistency
  - `eslint.config.mjs`, `prettier.config.cjs` for code quality
  - `tsconfig.json` with strict settings
  - `vitest.config.ts` for testing
  - `.env.example` as template, `.env.local` for local dev

## Bank/insurance alignment
- Digital front door, proactive nudges, and exportable evidence align with DB housing journey and GTM housing positioning.

## Risks & mitigations
- **Parsing quality** → human-readable “Confidence” flags; allow user corrections.
- **Data rights** → explicit per-home consent; granular scopes for partners.
- **Churn sensitivity** → transparent cost bands and clear advice surfaces.
