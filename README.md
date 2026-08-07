# NVDA MEDIA — Website

Premium, dark-theme, glassmorphism portfolio site for NVDA MEDIA. Pure HTML5 / CSS3 / vanilla JS — no frameworks, no backend.

## ⭐ Customize your site (start here)

**Edit `js/config.js` first.** It's the one file most changes go through — brand name, email, phone, WhatsApp, Instagram, LinkedIn, address, business hours and the footer description are all defined there once and applied automatically to all 9 pages (logo, footer, contact page, social icons everywhere). No need to hunt through every HTML file anymore.

Open `js/config.js`, change the values inside `window.SITE_CONFIG = { ... }`, save, refresh — done.

For everything else:
- **Colors** → top of `css/style.css`, the `:root { --bg: ...; --accent: ...; }` block.
- **Hero headline/subheadline** → `index.html`, inside the `<section class="hero">` block (one-off, not repeated elsewhere).
- **Page titles / meta descriptions** → each page's `<title>` and `<meta name="description">` (kept per-page on purpose, for SEO).
- **Services, pricing text, team names, timeline** → edit directly in `services.html`, `pricing.html`, `about.html`.
- **Portfolio projects** → `js/portfolio.js`, the `PROJECTS` array — add one object per project, nothing else to touch.

## Deploy to Vercel

1. Push this folder to a GitHub repo (or drag-and-drop the folder into the Vercel dashboard).
2. In Vercel: **New Project → Import** the repo.
3. Framework preset: **Other** (static site). No build command needed — leave "Build Command" and "Output Directory" blank/default.
4. Deploy. Your site will be live at `your-project.vercel.app`.

Or via CLI, from inside this folder:

```bash
npm i -g vercel
vercel
```

## Adding real video content

- Drop hero background video at `assets/videos/hero-reel.mp4` (looping, muted, ~15–30s, under ~8MB for fast load).
- Portfolio videos live in `assets/videos/` and are wired to project cards in **`js/portfolio.js`** — that file is the single source of truth. To add a project, add one object to the `PROJECTS` array with a title, category, video path, and two hex tones for the placeholder gradient before the video loads. No HTML editing required.
- Until real videos are added, thumbnails render as tasteful dark gradient placeholders — the site works fully without any assets.

## File structure

```
index.html / portfolio.html / services.html / pricing.html / about.html / contact.html
privacy.html / terms.html / 404.html
css/style.css        → base styles, tokens, components
css/responsive.css   → breakpoints
js/main.js           → nav, forms, FAQ accordion
js/animations.js     → scroll reveals, cursor, counters, testimonials slider
js/portfolio.js      → project data + grid/filter/search/lightbox logic
assets/videos/ | assets/images/ | assets/icons/ | assets/fonts/
```

## Notes

- Contact form currently simulates submission client-side (no backend). To make it functional, wire `js/main.js`'s `contactForm` submit handler to a service like Formspree, or add a Vercel Serverless Function.
- Google Maps embed and social links in `contact.html` / footer use placeholder addresses/handles — replace with your real ones.
- Colors, spacing and radii are defined as CSS custom properties at the top of `css/style.css` for easy re-theming.
