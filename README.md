# Arabic Age Guide

A small Arabic RTL static site about age calculation in the Gregorian and Hijri calendars. The site is plain HTML and CSS, with no build step and no server-side code.

Live site:

```text
https://arabic-age-render.guestblogger3699.workers.dev
```

## Files

- `index.html`: the homepage article and FAQ.
- `style.css`: typography and layout.
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

The Worker name is `arabic-age-render`. The configuration uses the repository root as the asset directory, while `.assetsignore` excludes `.git`, `.wrangler`, `README.md`, and other non-public files.

## Push updates to GitHub

The project is already a Git repository with the `main` branch connected to:

```text
https://github.com/gregorianagecalculator/arabic-age-render
```

For future updates:

```bash
git add .
git commit -m "Update site content"
git push
```

## Optional: Render deployment

Render requires a payment method on the account even for free static sites. If a card is added, the CLI flow is:

```bash
render login
render skills install --tool opencode --skill render-deploy
render services create --name arabic-age-render --type static_site --repo https://github.com/gregorianagecalculator/arabic-age-render --publish-directory . --branch main --confirm
```

Static sites do not accept the `--plan free` flag. They are free by default.
