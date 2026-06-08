# Putting the demo on GitHub Pages

**Short answer: yes — it's ready, and it's fully functional with dummy data.**

The site is a single self-contained `index.html` (all styles, scripts, and sample content are inside it; fonts load from Google's CDN). Everything interactive works on GitHub Pages: the live Sunday countdown, the Plan-a-Visit pop-up, the Prayer Wall (type and post), the podcast play buttons, and all navigation.

### The one nuance to know

GitHub Pages only serves **static** files — it can't run the `api/social.js` server function. That function is what pulls your *real* Facebook + Instagram posts. On GitHub Pages it simply won't be there, so the "This Week at East End" strip shows its **sample tiles** instead. That's by design — the page is built to fall back gracefully, so nothing looks broken. Everything else is real and working.

> If you later want the live social feed, host the exact same `index.html` on **Vercel** instead (it runs the `api/social.js` function too — see `DEPLOY-social-feed.md`). GitHub Pages is perfect for the demo; Vercel is the upgrade path when you want live data.

---

## Steps (about 5 minutes)

1. Create a free account at **github.com** if you don't have one.
2. Click **New repository** → name it something like `eastend-demo` → set it **Public** → Create.
3. On the repo page, click **Add file → Upload files**, and drag in **`index.html`**. Commit.
4. Go to **Settings → Pages** (left sidebar).
5. Under **Build and deployment → Source**, choose **Deploy from a branch**. Pick branch **`main`** and folder **`/ (root)`**. Save.
6. Wait ~1 minute. The page refreshes with your live URL:
   **`https://YOUR-USERNAME.github.io/eastend-demo/`**

Send that link to Pastor Dave — it works on his phone, no login needed.

---

## Even faster, if you just want a link tonight

Drag `index.html` onto **app.netlify.com/drop** — instant public URL, no account, no repo. (Same static behavior: sample tiles for the social strip, everything else live.)

---

## What's real vs. dummy on the deployed site

**Fully working:** design + animations, Sunday countdown, Plan-a-Visit pop-up, Prayer Wall, podcast play buttons, all menus and links, YouTube links (point to your real `@eastend4209` channel).

**Dummy/sample (clearly labeled in the UI):** latest sermon + summary, song list, events, podcast episodes, Pastor's Corner posts, the Facebook/Instagram strip, stories, and prayer examples. Pastor David's bio is placeholder text awaiting his real story + photo.

None of the dummy content errors or looks broken — it's all styled, realistic, and ready to swap for the real thing.
