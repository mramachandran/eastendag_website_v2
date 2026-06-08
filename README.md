# Deploying the live "This Week" feed

This turns the sample social tiles on the site into your real, auto-updating Facebook + Instagram posts. You need three files and three environment variables. Setup is ~30–45 min, mostly one-time Meta account work.

> First get your token and IDs by following **eastend-social-feed-setup.md** (the one-time Meta app + token steps). This guide just covers *deploying* the code once you have them.

---

## Files in this bundle

| File you have | Where it goes in your project |
|---|---|
| `api-social.js` | rename to **`api/social.js`** (a folder named `api`, file named `social.js`) |
| `env.example.txt` | reference only — values go into your host's Environment Variables |
| `eastend-redesign.html` | your site (rename to **`index.html`** when you deploy) |

Project layout:

```
your-project/
├── index.html        ← the site (eastend-redesign.html, renamed)
└── api/
    └── social.js     ← the serverless function (api-social.js, renamed)
```

---

## Option A — Vercel (recommended, the `api/` path just works)

1. Create a free account at **vercel.com** and install the Vercel CLI, or use the web "Import Project."
2. Put `index.html` and `api/social.js` in a folder (or a GitHub repo).
3. In the Vercel project → **Settings → Environment Variables**, add:
   - `META_PAGE_TOKEN`
   - `FB_PAGE_ID`
   - `IG_USER_ID` (optional)
   - `GRAPH_VERSION` (e.g. `v21.0`)
4. Deploy. Your site is live; the page automatically calls `/api/social` and swaps in real posts.

That's it — Vercel turns anything in `/api` into a serverless endpoint, so `api/social.js` becomes `https://yoursite/api/social` with no extra config.

---

## Option B — Netlify

Netlify uses a slightly different path. Two small changes:

1. Put the function at **`netlify/functions/social.js`** instead, and change the last line of the file from
   `export default async function handler(req, res) { ... }`
   to Netlify's signature:
   ```js
   export const handler = async () => {
     // ...same logic...
     return { statusCode: 200, body: JSON.stringify({ items }) };
   };
   ```
   (Use `return { statusCode: 200, body: JSON.stringify(...) }` instead of `res.status(200).json(...)`.)
2. Add a redirect so the page can still call `/api/social`. Create a `netlify.toml`:
   ```toml
   [[redirects]]
     from = "/api/social"
     to = "/.netlify/functions/social"
     status = 200
   ```
3. Add the same Environment Variables in **Site settings → Environment variables**, then deploy.

---

## How to confirm it's working

- Visit `https://yoursite/api/social` directly — you should see JSON like `{"items":[ ... ]}`.
- If you see `{"items":[],"error":"not configured"}`, an environment variable is missing.
- If the page shows sample tiles, the feed is just unavailable — the site is built to never break; it keeps the samples and tries again later (30-min cache).

---

## Security reminders

- The token only ever lives in the host's Environment Variables — it is **never** in `index.html` or visible to visitors.
- Prefer a **System User token** (Meta Business Settings) so it doesn't expire and isn't tied to one person's login.
- If a token leaks, revoke it in Business Settings and regenerate.
