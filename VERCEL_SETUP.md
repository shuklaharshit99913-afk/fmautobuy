# Vercel deployment

## Build
- Framework: Vite
- Build Command: `npm run build`
- Output Directory: `dist`
- Node: 20.19+ (Vite 8 requirement)

The `api/[...path].ts` function serves the existing Express `/api/*` routes.

## Required environment variables
- `DATABASE_URL` = your Neon PostgreSQL connection string
- `ZAPPAY_API_KEY` = your ZapPay API key
- `ZAPPAY_BASE_URL` = your ZapPay API base URL
- `ADMIN_EMAIL`
- `ADMIN_PASSWORD`

Do not commit real credentials to Git.
