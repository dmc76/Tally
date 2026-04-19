# Tally

A calm, minimal way to keep tabs on your recurring payments.

This folder is a **ready-to-deploy Progressive Web App**. No build step, no bundler — just drop it on Netlify and it works. Once deployed, it installs on Android and iPhone like a native app.

---

## What's in here

```
tally-deploy/
├── index.html        ← the whole app (React + Babel via CDN, inline JSX)
├── manifest.json     ← PWA manifest (name, icons, colors)
├── sw.js             ← service worker (offline support)
├── netlify.toml      ← Netlify config (headers, SPA fallback)
└── icons/            ← app icons (192, 512, maskable, apple-touch)
```

---

## Deploy to Netlify (2 minutes)

**Option A — Drag and drop (easiest):**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag this entire `tally-deploy` folder onto the drop zone
3. Netlify gives you a live HTTPS URL within seconds

**Option B — Git-connected:**
1. Push this folder to a GitHub repo
2. In Netlify: *Add new site → Import an existing project*
3. Pick the repo. No build command needed. Publish directory: `/` (or the subfolder)

HTTPS is automatic and required — PWAs won't install without it.

---

## Install on your phone

### Android (Chrome or Edge)
1. Open your Netlify URL in Chrome
2. Tap the **⋮ menu** → **Install app** (or "Add to Home screen")
3. Confirm. Tally now lives on your home screen like any other app.

### iPhone / iPad (Safari only — not Chrome on iOS)
1. Open your Netlify URL in **Safari**
2. Tap the **Share** button (square with an arrow)
3. Scroll down → **Add to Home Screen**
4. Tap **Add**. Done.

On both platforms it launches full-screen with no browser chrome, respects safe areas (notches, home indicator), and works offline after the first load.

---

## Customising

- **App name / colors** → edit `manifest.json`
- **Icons** → replace the PNGs in `icons/` (keep the same filenames and sizes)
- **The app itself** → edit the JSX inside `<script type="text/babel">` in `index.html`

When you ship an update, bump the `CACHE_NAME` in `sw.js` (e.g. `tally-v1` → `tally-v2`) so returning users get the new version.

---

## Notes

- Data is stored locally on your device via `localStorage`. Nothing is sent to a server.
- Works offline after the first visit (service worker caches the shell).
- For a production-grade app you'd want: a real build step (Vite), code-splitting, and optionally cloud sync. This prototype stays single-file on purpose so you can see everything.
