# Arabic Age Guide

A small Arabic RTL static site about age calculation in the Gregorian and Hijri calendars. The site is plain HTML and CSS, with no build step and no server-side code.

## Files

- `index.html`: the homepage article and FAQ.
- `style.css`: typography and layout.
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

## Push to GitHub

This directory is already a Git repository with an initial commit on the `main` branch.

1. Create a new public repository on GitHub named `arabic-age-render`.
2. Add the remote and push:

```bash
git remote add origin https://github.com/YOUR_USERNAME/arabic-age-render.git
git push -u origin main
```

If the remote already exists, update it instead:

```bash
git remote set-url origin https://github.com/YOUR_USERNAME/arabic-age-render.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

## Deploy to Render

### 1. Install the Render CLI

On Windows:

```powershell
winget install --id Render.CLI --exact --accept-source-agreements --accept-package-agreements
```

Verify the installation:

```bash
render --version
```

### 2. Install the OpenCode Render skill

```bash
render skills install --tool opencode --skill render-deploy
```

### 3. Log in to Render

```bash
render login
```

Complete the browser login flow. If you already have an authenticated Render CLI session, you can skip this step.

### 4. Create the static site

Use the HTTPS URL of the GitHub repository you created:

```bash
render services create --name arabic-age-render --type static_site --repo https://github.com/YOUR_USERNAME/arabic-age-render.git --publish-directory . --plan free
```

Settings used by this command:

- Service type: Static Site
- Plan: Free
- Branch: `main`
- Publish directory: `.`
- Build command: leave empty

The publish directory is `.` because `index.html` is at the root of the repository.

### 5. Open the site

When the deployment finishes, Render prints the public URL. It will look like:

```text
https://arabic-age-render.onrender.com
```

You can also find the service in the Render Dashboard under your workspace.

## Updating the site

After changing any file:

```bash
git add .
git commit -m "Update site content"
git push
```

Render can redeploy automatically after each push if auto deploy is enabled for the service. Otherwise, trigger a deploy from the Render Dashboard or with the Render CLI.
