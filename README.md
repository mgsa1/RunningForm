# RunningForm

AI-powered running form analysis. Upload a short video, get structured coaching feedback and drill recommendations.

## How it works

1. Upload a running video (mobile or desktop)
2. The browser extracts frames using the Canvas API — no raw video is ever stored
3. Frames are sent to Claude Sonnet for analysis
4. Results include form observations, severity ratings, and targeted drills

## Tech stack

- **Framework:** Next.js 14 App Router (TypeScript)
- **Auth + DB + Storage:** Supabase
- **AI:** Anthropic Claude Sonnet
- **Job queue:** Inngest
- **Hosting:** Vercel

## Local development

```bash
cp .env.example .env.local
# Fill in your keys in .env.local

npm install
npm run dev
```

Required environment variables (see `.env.example`):

| Variable | Where to get it |
|---|---|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase project settings → API |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase project settings → API |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase project settings → API |
| `ANTHROPIC_API_KEY` | console.anthropic.com |
| `INNGEST_SIGNING_KEY` | Inngest dashboard |
| `INNGEST_EVENT_KEY` | Inngest dashboard |

## Database

Run migrations in order:

```bash
supabase db push
# or apply manually via the Supabase SQL editor:
# supabase/migrations/001_initial.sql
# supabase/migrations/002_storage_policies.sql
# supabase/migrations/003_add_runner_context.sql
```

## Disclaimer

AI-generated analysis is intended for educational purposes only. It is not a substitute for advice from a qualified running coach or physiotherapist.
