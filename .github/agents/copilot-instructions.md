# Build Minds Website - AI Agent Instructions

## Project Overview

Build Minds is a **content company** (not a software house / SaaS vendor). This repo is its public website and blog: content about software development, DevOps, and AI. Static site, built with Eleventy (11ty), Markdown content, deployed to GitHub Pages via GitHub Actions.

**Key context:**
- Language: Italian throughout (content, UI copy).
- No client-facing services are sold here — no "servizi"/"portfolio" sales pages. Don't reintroduce a lead-gen/consulting framing.
- Legal entity: Build Minds di Luca Fontana (P.IVA 14537670961) — keep this in the footer; it's real, not a placeholder.

## Structure & Conventions

```
src/
  _includes/base.njk   # shared header/nav/footer
  _includes/page.njk    # generic content page layout (hero + article-content)
  _includes/post.njk    # blog post layout (hero + meta + article-content)
  assets/                # style.css, logo, blog images — passthrough-copied as-is
  posts/*.md             # blog posts, one file per post, front matter: layout, title, subtitle, date, excerpt, readingTime
  index.njk, blog.njk, chi-siamo.md, contatti.md, privacy-policy.md, cookie-policy.md
.eleventy.js
```

- CSS design system (colors, fonts, breakpoints) lives in `src/assets/style.css`, inherited from the original site — reuse existing classes (`.hero`, `.section`, `.section-alt`, `.blog-card`, `.article-content`, `.btn`, etc.) rather than inventing new ones.
- Publishing a post = adding a Markdown file to `src/posts/` and pushing to `main`. See `README.md` for the exact front matter format.
- No build step is manual: `deploy.yml` builds and publishes on every push to `main`; `ci.yml` builds on every other push/PR to catch breakage early.

## Anti-Patterns to Avoid

- Don't add "servizi"/"portfolio"/consulting-sales pages — that was the previous (pre-pivot) business model and no longer reflects the company.
- Don't hardcode colors — use CSS variables in `style.css`.
- Don't add a JS framework or build tool beyond Eleventy — keep it low-maintenance.
- Don't wire up a contact form or analytics without updating `privacy-policy.md` / `cookie-policy.md` first (currently accurate: no tracking, no form).

---

**Last updated:** 2026-07-23 | **Stack:** Eleventy (11ty) → GitHub Pages via GitHub Actions
