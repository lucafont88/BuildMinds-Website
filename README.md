# Build Minds — Website & Blog

Public site and blog for Build Minds: content about software development, DevOps, and AI.

Static site built with [Eleventy (11ty)](https://www.11ty.dev/), Markdown-based content, deployed to GitHub Pages via GitHub Actions.

## Structure

```
src/
  _includes/       # layouts (base.njk, page.njk, post.njk)
  assets/          # style.css, logo, blog images (copied as-is)
  posts/           # blog posts (Markdown, one file per post)
  index.njk        # homepage
  blog.njk          # blog index (auto-lists posts/)
  chi-siamo.md, contatti.md, privacy-policy.md, cookie-policy.md
.eleventy.js       # Eleventy config
.github/workflows/
  ci.yml           # builds on every branch push / PR — catches broken builds before merge
  deploy.yml       # builds and deploys to GitHub Pages on push to main
```

## Publish a new blog post

1. Add a new file in `src/posts/`, named `YYYY-MM-DD-slug.md`.
2. Add front matter:
   ```yaml
   ---
   layout: post.njk
   title: Post Title
   subtitle: Optional subtitle
   date: 2026-01-15
   excerpt: One-sentence summary shown on the blog index and homepage.
   readingTime: 5 min lettura
   ---
   ```
3. Write the post body in Markdown below the front matter.
4. Commit and push to `main` (or merge a PR into `main`).

That's it — the `Deploy` GitHub Actions workflow builds the site and publishes it automatically. No manual build/upload step.

## Local development

```
npm install
npm run serve   # local dev server with live reload
npm run build    # production build to _site/
```

## CI/CD

- **Any push / PR**: `ci.yml` runs `npm run build` to catch broken builds early.
- **Push to `main`**: `deploy.yml` builds and publishes to GitHub Pages (site is live at the repo's Pages URL, see repo settings for the exact domain).

## Notes for whoever edits this next

- Repo is public — required for GitHub Pages on the free tier. There are no secrets in this repo; keep it that way.
- No paid hosting/vendor is in use (GitHub Pages, free). If a custom domain or a headless CMS is wanted later, flag the cost/vendor decision before adopting it.
- No contact form or analytics are wired up yet — `privacy-policy.md` / `cookie-policy.md` reflect that; update them if either is added.
