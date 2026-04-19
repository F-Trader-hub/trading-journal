# Trading Journal — Local Setup

A personal trading journal built with **React 18 + Vite + TypeScript + Tailwind + shadcn/ui**, with **Supabase** (Lovable Cloud) for auth, database, and storage.

## Features
- Email/password authentication
- Trade logging (pair, direction, entry/exit, SL/TP, RR, strategy, session, emotions, notes)
- Screenshot uploads (HTF / MTF / LTF)
- Stats: Equity Curve, Strategy Breakdown, Session Breakdown, Daily Heatmap, Monthly Performance
- Backup / Restore (JSON)
- Light/Dark theme
- Responsive (mobile-friendly with FAB)

## Prerequisites
- **Node.js 18+** (recommended 20+) — https://nodejs.org
- **npm**, **pnpm**, or **bun**

## 1. Install dependencies
```bash
npm install
# or
bun install
```

## 2. Environment variables
Create a `.env` file in the project root with your Supabase project credentials:

```env
VITE_SUPABASE_URL=https://YOUR_PROJECT_REF.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=YOUR_ANON_PUBLIC_KEY
VITE_SUPABASE_PROJECT_ID=YOUR_PROJECT_REF
```

> The current `.env` shipped with this export already points to the Lovable Cloud backend used in development. To use your own Supabase project, replace the values and re-run the migrations in `supabase/migrations/` against your project.

## 3. Run locally (dev server)
```bash
npm run dev
```
Open http://localhost:8080

## 4. Build for production
```bash
npm run build
npm run preview   # preview the production build locally
```
Output goes to `dist/`. Deploy to any static host (Vercel, Netlify, Cloudflare Pages, S3, etc.).

## 5. Lint & test
```bash
npm run lint
npm test
```

## Database setup (if using your own Supabase project)
1. Create a new project at https://supabase.com
2. Run all SQL files in `supabase/migrations/` (in order, oldest first) via SQL Editor
3. Update `.env` with the new project URL + anon key
4. (Optional) Configure auth providers in Supabase dashboard

## Project structure
```
src/
├── components/        # UI components (shadcn + custom)
├── hooks/             # useAuth, useTrades, usePrefs, useTheme
├── lib/               # backup, format, image, pnl, utils
├── pages/             # Index, Auth, NotFound
├── integrations/
│   └── supabase/      # auto-generated client + types
├── types/             # Trade, Session, etc.
└── index.css          # design tokens (HSL semantic colors)
supabase/
├── config.toml
└── migrations/        # SQL schema
```

## Tech stack
- React 18, Vite 5, TypeScript 5
- Tailwind CSS v3 + shadcn/ui (Radix primitives)
- React Router 6, TanStack Query
- Recharts (charts)
- Supabase JS v2 (auth + Postgres + storage)
- Sonner (toasts), Lucide (icons), date-fns
- Vitest + Testing Library
