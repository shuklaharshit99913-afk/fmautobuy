# Flipkart Mart — publish setup

This build uses Neon PostgreSQL as the runtime source of truth and ZapPay UPI server-side.

## Netlify environment variables
Set these in Netlify Site configuration (do NOT commit secrets):

- `DATABASE_URL` = your Neon PostgreSQL connection string
- `ZAPPAY_API_KEY` = your ZapPay Developer API key
- `ZAPPAY_BASE_URL` = `https://zappay-beta.vercel.app`
- `ADMIN_EMAIL` = your admin email
- `ADMIN_PASSWORD` = your admin password
- `SESSION_SECRET` = a long random secret
- `STORE_URL` = your deployed store URL

The repository intentionally does not contain the supplied database password or ZapPay secret.

## Deploy
1. Upload/push this folder to Netlify.
2. Build command: `npm run build`.
3. Publish directory: `dist`.
4. Add the environment variables above.
5. Deploy.
6. Open `/api/health` and confirm `postgresConnected: true` and `zappayConfigured: true`.

Product image URLs and uploaded images are stored in the product JSON record, so they persist across devices. Product/catalog changes are refreshed every 2.5 seconds from PostgreSQL.

Checkout accepts ZapPay UPI only. Payment fulfillment occurs only after the server independently verifies ZapPay order status as `success`.
