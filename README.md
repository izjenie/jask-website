# JAS Kapital Website

Static website for JAS Kapital. This repository contains a simple HTML/CSS site that can be hosted on any static hosting provider.

## Project structure

- `index.html`
- `about.html`
- `portfolio.html`
- `styles.css`
- `assets/`

## Local preview

- Open `index.html` directly in a browser, or
- Use a simple static server (optional):

```bash
npx serve .
```

## Make it live on jaskapital.com

This is a static site. The simplest, reliable path is Netlify (recommended). Alternatives for Vercel, GitHub Pages, and Cloudflare Pages are included below.

### Option A — Netlify (recommended)

1. Create a Netlify account and “Add new site” → “Import from Git”. Select this repository.
2. Build settings:
   - Build command: none
   - Publish directory: `.` (repository root)
3. Deploy the site. Netlify will give you a temporary domain like `your-site.netlify.app`.
4. Add custom domains in Netlify → Site settings → Domain management:
   - Add `jaskapital.com`
   - Add `www.jaskapital.com`
5. Configure DNS at your domain registrar (if NOT using Netlify DNS):
   - Root/apex (`jaskapital.com`): A → 75.2.60.5 and 99.83.190.102
   - `www.jaskapital.com`: CNAME → your-site.netlify.app

Notes:
- If you transfer DNS to Netlify DNS, they will provide nameservers and manage the above automatically.
- The A record IPs are Netlify’s load balancers; verify in Netlify’s Domain panel in case they change.

### Option B — Vercel

1. Create a Vercel project → “Import Git Repository”.
2. Framework preset: “Other”/“Static”. Build command: none. Output/public directory: `.`
3. After first deploy, go to Settings → Domains and add:
   - `jaskapital.com`
   - `www.jaskapital.com`
4. Configure DNS at your registrar:
   - Root/apex (`jaskapital.com`): A → 76.76.21.21
   - `www.jaskapital.com`: CNAME → `cname.vercel-dns.com`

### Option C — GitHub Pages

1. Push this repo to GitHub.
2. GitHub → Repository → Settings → Pages:
   - Source: Deploy from a branch → `main`/`master` → `/` (root)
3. Create a `CNAME` file in the repo root containing:

```
jaskapital.com
www.jaskapital.com
```

4. Configure DNS at your registrar:
   - Root/apex (`jaskapital.com`): A → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
   - `www.jaskapital.com`: CNAME → `<your-username>.github.io`

### Option D — Cloudflare Pages

1. Create a Pages project and connect this repository.
2. Build command: none. Build output directory: `.`
3. After deploy, add custom domains:
   - `jaskapital.com`
   - `www.jaskapital.com`
4. Configure DNS in Cloudflare DNS (recommended) or your registrar:
   - `www.jaskapital.com`: CNAME → your `*.pages.dev` domain
   - Root/apex: CNAME flattening to the same `*.pages.dev` target (Cloudflare DNS supports CNAME flattening at apex) or use Cloudflare Pages’ suggested A/ALIAS target.

## Production checklist

- Favicon and meta tags set in `index.html`.
- `robots.txt` and `sitemap.xml` (optional for SEO).
- Redirects (if needed) via provider config (e.g., Netlify `_redirects`).
- Enforce HTTPS and non-www/www canonical (via provider’s domain settings).

## Updating the site

- Commit and push changes to the default branch. Your hosting provider will auto-deploy.
