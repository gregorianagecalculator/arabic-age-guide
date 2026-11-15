# Arabic Age Guide

A small Arabic RTL static site about age calculation in the Gregorian and Hijri calendars. The site is plain HTML and CSS, with no build step and no server-side code.

Live site:

```text
https://arabic-age-guide.lujain.workers.dev
```

## Search Console

The Google Search Console verification meta tag is in the `<head>` of `index.html`.

Sitemap:

```text
https://arabic-age-guide.lujain.workers.dev/sitemap.xml
```

## Files

- `index.html`: the homepage article and FAQ.
- `style.css`: typography, layout, dark mode, and responsive design.
- `favicon.svg`: site icon.
- `sitemap.xml`: search engine sitemap.
- `robots.txt`: crawler rules and sitemap reference.
- `wrangler.jsonc`: Cloudflare Workers static asset configuration.
- `.assetsignore`: keeps repository and deployment files out of the public asset bundle.
- `README.md`: this deployment guide.

## Local preview

From this directory, run:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

## Deploy to Cloudflare Pages

This site is deployed with Wrangler to the latest Cloudflare Pages, which is now part of Cloudflare Workers. It runs as a static asset Worker on the free plan.

### 1. Install Node.js

Node.js 20 or newer is recommended.

### 2. Log in to Cloudflare

```bash
npx wrangler login
```

Complete the browser authorization flow.

### 3. Deploy

```bash
npx wrangler deploy
```

Wrangler reads `wrangler.jsonc`, uploads the static files, and prints the public URL.

### 4. Redeploy after changes

```bash
npx wrangler deploy
```

The Worker name is `arabic-age-guide`. The configuration uses the repository root as the asset directory, while `.assetsignore` excludes `.git`, `.wrangler`, `README.md`, and other non-public files.

## Push updates to GitHub

The project is already a Git repository with the `main` branch connected to:

```text
https://github.com/gregorianagecalculator/arabic-age-guide
```

For future updates:

```bash
git add .
git commit -m "Update site content"
git push
```
