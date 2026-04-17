# The Vinyl Vault

The Vinyl Vault is a mobile-first **digital vault for vinyl collectors**: scan records, auto-import rich metadata, track condition and value, log listening history, and share/trade with a community inspired by **The Vinyl Vault Show**.

## Product Goals

- Digitize records in under 60 seconds (scan + auto-metadata)
- Deliver accurate valuation and portfolio insights
- Support collector community, discovery, and trade workflows
- Provide a polished album-art-first UI with dark/light themes
- Ship as installable PWA plus native iOS/Android apps

## MVP Scope (Phase 1)

### 1) Cataloguing & Import
- Barcode/QR scanning (camera)
- Discogs metadata sync (artist, title, label, year, tracklist, genre, pressing, cover)
- CSV/JSON and Discogs collection import support

### 2) Condition & Inventory
- Goldmine grading (Mint → Poor)
- Photo evidence uploads + personal notes
- Search/filter/sort by artist, year, genre, value, last played, tags

### 3) Valuation & Portfolio
- Market value estimate from Discogs marketplace data
- Collection total value dashboard
- Basic value trend history and alerts

### 4) Listening & Engagement
- Play logs, ratings, reviews, notes
- The Vinyl Vault Show album highlights/feed integration

### 5) Accounts & Profiles
- Secure auth
- Private-first collection with optional public sharing

## Phase 2

- Collector-to-collector marketplace
- AI recommendations and cover recognition enhancements
- Advanced analytics and deeper social integrations
- Admin tools for show content and growth workflows

## Suggested Technical Architecture (TypeScript-first)

- **Monorepo**: Turborepo + pnpm workspaces
- **Client**: Expo (React Native + Web/PWA), React Native Web, optional Next.js dashboard
- **UI**: Tailwind CSS + NativeWind + shadcn/ui + Tamagui
- **State**: Zustand + TanStack Query + Supabase Realtime
- **Scanning**: react-native-vision-camera (ML Kit / Vision), web fallback via ZXing
- **Backend**: Supabase (Postgres, Auth, Storage, Realtime, Edge Functions)
- **Cache/Jobs**: Upstash Redis + scheduled jobs (Supabase cron / Inngest)
- **Integrations**: Discogs API, Bluesky ATProto, Stripe (future)
- **Quality**: Jest, React Native Testing Library, Playwright, Sentry, PostHog
- **Deploy**: Expo EAS + Vercel + Supabase

## Non-Functional Requirements

- Mobile-first responsive UX
- Installable PWA with offline-first behavior
- GDPR-aligned privacy and secure authentication
- Scalable architecture for 10k+ users and millions of records
- Rate-limit-safe API integration and caching

## Success Metrics

- 5,000 active collectors in Year 1
- Average collection size >150 records
- 85%+ retention via Vault Show engagement
- Positive NPS, especially among record-fair users

## Getting Started (Implementation Plan)

1. Initialize monorepo with `pnpm` + `turbo`
2. Scaffold Expo app for iOS/Android/Web
3. Configure Supabase project, schema, auth, storage, and edge functions
4. Implement barcode scan flow + Discogs metadata ingest
5. Add collection CRUD, grading workflow, and valuation dashboard
6. Add listening logs, profile privacy settings, and Vault Show feed
7. Add tests for scan/import, value calculations, and key user journeys

---

This repository currently contains the product foundation/specification. The next milestone is scaffolding the monorepo and shipping the first end-to-end “scan → save record” workflow.
