# Smart NFC Guest Pass — Landing Page

Premium multilingual landing page for the Hostfully Marketplace Add-On.

---

## 🌍 Language Support

| Code | Language | URL param |
|------|----------|-----------|
| `en` | English (default) | `?lang=en` |
| `es` | Spanish | `?lang=es` |
| `fr` | French | `?lang=fr` |
| `de` | German | `?lang=de` |
| `nl` | Dutch | `?lang=nl` |

Language is detected in this priority order:
1. `?lang=` URL parameter
2. `localStorage` (user's last choice)
3. Browser's preferred language
4. Fallback: English

---

## 📁 File Structure

```
/
├── index.html          ← Single-file production page (all-in-one)
└── README.md           ← This file
```

The entire page is **one self-contained HTML file** — no build step, no Node.js, no dependencies beyond Tailwind CDN and Google Fonts.

---

## 🔧 Where to Edit

### Change CTA link (Hostfully Marketplace URL)
Search for this comment in `index.html`:
```
<!-- CTA LINK — change href to your Hostfully Marketplace URL -->
```
Update the `href` on both CTA anchor tags.

### Edit translations / add a language
Find the `TRANSLATIONS` object near the bottom of `index.html`.
To add a new language (e.g., Italian):
1. Add `"it": { ... }` copying all keys from `"en"` and translating values
2. Add a button in the `#lang-switcher` nav div: `<button class="lang-btn" data-lang="it" onclick="setLang('it')">IT</button>`

### Update branding
- **Logo name**: Search `Smart NFC` in the nav section
- **Colors**: Edit Tailwind config at top of `<script>` block or CSS variables in `<style>`
- **Footer links**: Search `FOOTER LINKS` comment

### Change footer / legal links
Search for `FOOTER LINKS` comment in the HTML.

---

## 🚀 Deployment

### Option 1 — Vercel (recommended, free)
```bash
npm i -g vercel
# drag the folder to vercel.com/new  OR:
vercel deploy --prod
```

### Option 2 — Netlify (free)
```bash
# Drag-and-drop the index.html to netlify.com/drop
# OR via CLI:
npm i -g netlify-cli
netlify deploy --prod --dir .
```

### Option 3 — Cloudflare Pages (free)
1. Push to GitHub repo
2. Connect at dash.cloudflare.com → Pages → Connect to Git
3. Build command: *(none)*  |  Output directory: `.` or `/`

### Option 4 — GitHub Pages (free)
1. Push `index.html` to a GitHub repo root
2. Settings → Pages → Branch: `main` → Folder: `/ (root)`
3. Your site is live at `https://username.github.io/repo-name/`

---

## ⚡ Performance Notes
- No JavaScript frameworks — pure vanilla JS
- Tailwind loaded from CDN (production: replace with purged local build for max perf)
- Google Fonts preconnected for fast load
- Single HTTP request for the full page

---

## 🧩 Tech Stack
- **HTML5** semantic markup
- **Tailwind CSS** (CDN) for utility styling
- **Google Fonts**: Syne (display) + DM Sans (body)
- **Vanilla JS** i18n engine with localStorage + URL params
- **IntersectionObserver** for scroll-triggered animations
- Zero backend, zero build step, zero dependencies to install
