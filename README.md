# Salaam Japan V6 - Cloud OCR

## What changed
- OCR runs server-side through Google Cloud Vision `DOCUMENT_TEXT_DETECTION` with Japanese language hint.
- Japanese text is translated to Indonesian with Cloud Translation Basic v2.
- The browser never receives the Google API key.
- The same API works on laptop, Android, and iPhone.

## Google Cloud setup
1. Create/select a Google Cloud project and attach billing.
2. Enable **Cloud Vision API** and **Cloud Translation API**.
3. Create an API key in APIs & Services > Credentials.
4. Restrict the key to only those two APIs. Do not commit the key to GitHub.

## Cloudflare secret
In Cloudflare Dashboard: Workers & Pages > `salaam-japan` > Settings > Variables and Secrets > Add.
- Type: Secret
- Name: `GOOGLE_API_KEY`
- Value: your Google API key

Or with Wrangler:
```bash
npx wrangler secret put GOOGLE_API_KEY
```

## Deploy via GitHub
Replace the repository contents with this package and commit to `main`. If the Worker is connected to GitHub, Cloudflare builds automatically.

Build settings:
- Build command: `npm run deploy` only when using Workers Builds as configured by Cloudflare; otherwise use the existing Workers Git deployment defaults.
- Deploy command: `npx wrangler deploy`

## Test
Use a Japanese label showing `原材料名：牛乳100%`. Expected translation: roughly `Komposisi: 100% susu sapi`, with a yellow result because absence of risky keywords is not halal certification.
