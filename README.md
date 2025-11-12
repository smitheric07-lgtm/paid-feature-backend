# Paid Feature Backend (Next.js + Vercel + Resend + Cron)

Implements:
- FREE & PAID email delivery (Resend)
- Cash App via email-parser ingestion (Option B) + Square Checkout (Option A)
- Weekly reminders via Vercel Cron
- Partner Data API pull from PARTNER_DATA_URL

## Quick Start
1) `npm i`
2) Copy `.env.example` → `.env` and fill values
3) `npx prisma generate && npx prisma db push`
4) `npm run dev`

## Routes
- POST `/api/subscribe` { email, plan: 'free'|'paid' }
- POST `/api/payments/square/checkout` { email } → returns { url }
- POST `/api/webhooks/square` (Square dashboard webhook)
- POST `/api/payment/ingestEmail` (Zapier/Mailgun parser) with header `x-ingest-secret`
- GET `/api/cron/send-reminders` (invoked by Vercel cron)
