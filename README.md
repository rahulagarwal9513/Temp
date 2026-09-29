# CORNERPLAY

Cornerplay is a production-oriented starter for a **free-to-play social gaming and entertainment platform**. It intentionally excludes real-money gambling primitives.

## Non-negotiable product boundary

The database/API do not define deposits, withdrawals, bets, wagers, cash balances, crypto balances or cash-out requests. Gameplay progression uses score, XP, levels, achievements and cosmetic recognition only.

## Stack

- Next.js App Router + React + TypeScript
- Tailwind CSS + Lucide
- Supabase Auth + PostgreSQL + Row Level Security
- Zod API validation

## Local setup

1. Install Node.js LTS.
2. Create a Supabase project.
3. Run `supabase/schema.sql` in Supabase SQL Editor.
4. Copy `.env.example` to `.env.local` and add your Supabase URL/key.
5. Install dependencies: `npm install`.
6. Run `npm run dev`.
7. Open `http://localhost:3000`.

## Supabase Auth

Enable Email provider. For production, configure the project's Site URL and redirect URLs to your deployed domain and `/auth/callback`.

## Admin

Register a normal user first, then promote the user's `profiles.role` to `admin` using a controlled server-side/admin database process. Do not expose service-role keys to the browser.

## Production hardening checklist

- Use a dedicated Supabase production project.
- Configure custom SMTP and email verification.
- Add a real transactional email provider.
- Add application-level rate limiting (for example, an edge/WAF or managed rate-limit service) to login, registration, posting and score endpoints.
- Add automated abuse detection and moderation workflows.
- Review CSP and allowed image/connect domains after adding third-party services.
- Add observability, backups, incident response and dependency scanning.
- Complete legal/privacy/age-safety review for every jurisdiction in which the service is offered.
- Have qualified counsel review the final Terms, Privacy, age-gating and consumer-protection requirements before launch.

## Testing

`npm run typecheck`
`npm run build`

Add Playwright/Vitest coverage for authentication, authorization, score submission, tournament entry, moderation and account deletion before production launch.

## Game fairness

The included game UI is a non-monetary demo. Before publishing competitive games, implement and document deterministic/server-authoritative rules, seed handling where randomness is used, anti-cheat controls and reproducible score validation.
