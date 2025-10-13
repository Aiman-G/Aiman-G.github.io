# Multilingual GitHub Pages Blog (Hugo + PaperMod)

This starter is configured for **multiple languages** and **multiple topics** (e.g., Tech, Poetry). Deployed via GitHub Actions to GitHub Pages.

## Quick start

1. Download and unzip this project.
2. Replace placeholders:
   - `YOUR_USERNAME` → your GitHub username
   - `YOUR_NAME` → your name
3. Create a repo named **`YOUR_USERNAME.github.io`** and push to `main`.
4. In your repo: **Settings → Pages → Source = GitHub Actions**.
5. Visit `https://YOUR_USERNAME.github.io/`

## Multilingual content

- Content lives under `content/<lang>/...` (e.g., `content/en/`, `content/es/`).
- For translations of the same post, use the same `translationKey` in front matter.
- URLs will be `/en/...` and `/es/...` because `defaultContentLanguageInSubdir = true`.

### Add a new language
1. Duplicate the `content/en` folder as `content/<lang>`.
2. Add a new block under `[languages.<lang>]` in `hugo.toml`. Set `languageName`, `title`, menus, etc.
3. Add or translate posts. Keep a shared `translationKey` where they correspond.

## Topics (Tech, Poetry, ...)

- This starter uses **taxonomies**: `categories` and `tags`.
- Assign a category in each post front matter: `categories: ["tech"]` or `["poetry"]`.
- The menu links point to `/categories/tech/` and `/categories/poetry/` (automatically prefixed with the language subpath).

## Write a post

Example (English, Tech):
```yaml
---
title: "My First Tech Note"
date: 2025-10-03
translationKey: "first-tech-note"
categories: ["tech"]
tags: ["hugo", "notes"]
draft: false
---
Content in **Markdown**.
```

Spanish translation:
```yaml
---
title: "Mi primera nota técnica"
date: 2025-10-03
translationKey: "first-tech-note"
categories: ["tech"]
tags: ["hugo", "notas"]
draft: false
---
Contenido en **Markdown**.
```

## Customize

- **Home/profile card, menus, descriptions:** per-language in `hugo.toml`.
- **Styling:** `assets/css/extended/custom.css`.
- **Logo/Favicon:** put files in `static/` (e.g., `static/logo.png`).

## Local preview

Install Hugo Extended, then run:
```
hugo server -D
```
Visit `http://localhost:1313` (you'll see language selectors).

---
Built with ❤️ using Hugo and the PaperMod theme.