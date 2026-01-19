# Build Minds Website - AI Agent Instructions

## Project Overview
Build Minds is a **static website** for a software house targeting Italian PMIs (small/medium enterprises) in Vimercate, Lombardia. The site is purely HTML/CSS (no backend framework) and focuses on SEO, lead generation, and service promotion.

**Key Business Context:**
- **Target:** PMIs 10-100 employees in Lombardia
- **Primary revenue streams:** Custom software (60%), SaaS (20%), Consulting (15%), Training (5%)
- **Core value prop:** Fast turnaround, personalized solutions, competitive pricing vs. large software houses
- **Language:** Italian throughout (except code comments)

## Project Structure & Conventions

### File Organization
```
├── index.html           # Homepage (main landing page)
├── servizi.html         # Services overview with 4 service categories
├── chi-siamo.html       # About page with company mission
├── contatti.html        # Contact form & lead generation
├── blog.html            # Blog posts for SEO (Italian content)
├── portfolio.html       # Case studies (currently not linked, placeholder)
├── style.css            # Single CSS file with responsive design
├── logo-512.jpg         # Light logo for headers
└── logo-512-negative.jpg # Dark logo for favicon/dark backgrounds
```

### Architecture Patterns
1. **Semantic HTML structure** - Every page follows:
   - Header with sticky nav (active page highlighted)
   - Hero section (h1 title + subtitle)
   - Multiple content sections (section/section-alt for alternating backgrounds)
   - Footer (4-column layout: company, services, about, contact)
   - Mobile menu toggle (☰ button)

2. **CSS Design System** - CSS variables at root:
   ```css
   --primary-color: #2B7A9F;      /* Blue (CTAs) */
   --secondary-color: #1E3A5F;    /* Dark blue (headings) */
   --accent-color: #4AC4D4;       /* Teal (hover states) */
   --text-dark: #333333;
   --text-light: #666666;
   --bg-light: #F5F7FA;
   --white: #FFFFFF;
   ```
   Use these in all changes to maintain consistency.

3. **Typography**:
   - Headings: Poppins (700 weight, via Google Fonts)
   - Body: Inter (400-700 weights, via Google Fonts)
   - Always preconnect to `fonts.googleapis.com` and `fonts.gstatic.com`

4. **Responsive Breakpoint**: 768px (single mobile menu toggle, CSS grid auto-fit)

## Critical Developer Workflows

### Adding a New Service/Feature
1. **Content location**: Add in `servizi.html` with a unique `id` anchor (e.g., `id="service-name"`)
2. **Navigation link**: Update ALL pages' nav `<ul>` to include new section links
3. **Footer link**: Add to Servizi section in footer (all pages)
4. **Styling**: Add `.service-card` or relevant grid class to `style.css`
5. **SEO**: Update page title/meta tags in `<head>`

### Updating Contact Form
- Form is in `contatti.html`, currently `action="#"` (placeholder)
- To implement: Replace with Netlify Forms (`data-netlify="true"`) or Formspree endpoint
- Form fields: name, company, email, phone, service type, message, budget
- All HTML input IDs/names must match backend expectation

### Publishing Workflow
- **Hosting**: Netlify or Vercel (drag-and-drop deployment)
- **Domain**: buildminds.it (DNS pointing required)
- **SSL**: Automatic with Netlify/Vercel
- **No build step required** - Pure HTML/CSS deployment

## Code Patterns & Conventions

### HTML
- **Language attribute**: Always `lang="it"` (Italian site)
- **Navigation link highlighting**: Add `class="active"` to current page link in nav
- **Anchors for sections**: Use `id="section-name"` for deep linking from other pages
- **Always include**: Meta charset UTF-8, viewport, title, description, keywords, favicon link
- **CTA buttons**: Use `class="btn btn-primary"` or `class="btn btn-secondary"`
- **Placeholder text**: Marked as `+39 XXX XXX XXXX`, `XXXXXXXXXXX` for P.IVA (see README for full list)

### CSS
- **Selectors**: Class-based (no IDs for styling)
- **Mobile-first** media queries: Base styles mobile, `@media (min-width: 768px)` for desktop
- **Grid layouts**: Use `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))` for service cards
- **Shadows**: Use `var(--shadow)` and `var(--shadow-hover)` defined in `:root`
- **Transitions**: Default to `transition: all 0.3s ease` for hover states
- **No utility classes** - All styling in semantic classes (`.service-card`, `.value-item`, etc.)

### JavaScript
- Minimal use: Only mobile menu toggle
- Pattern: `document.querySelector('.mobile-menu-toggle').addEventListener('click', ...)`
- No frameworks used - pure vanilla JS

## Key Integration Points & Dependencies

### External Services (For Future Implementation)
1. **Form backend**: Netlify Forms (easiest), Formspree, or PHP handler
2. **Email collection**: Mailchimp/Brevo (blog newsletter signup)
3. **Analytics**: Google Analytics 4 (add to all pages before `</head>`)
4. **SEO**: Google Search Console + Google My Business
5. **Cookies**: iubenda or Cookiebot (required for GDPR compliance)

### Font Dependencies
- Google Fonts: Inter + Poppins
- **Preconnect to** `https://fonts.googleapis.com` and `https://fonts.gstatic.com` (already in all pages)

## Content & SEO Specifics

### Language & Localization
- **All text in Italian** - User audience is Italian PMIs
- **Geographic focus**: Vimercate, Monza-Brianza, Lombardia (keywords in meta tags)
- **Sector keywords**: manifattura, retail, sanità, logistica (in Services section)

### SEO Best Practices Implemented
- Unique title + meta description on each page (50-60 chars for title, 150-160 for description)
- Keywords targeting "software house vimercate", "sviluppo software custom", "consulenza IT"
- No meta robots restrictions - site should be indexed
- Internal linking via `.service-link` and footer links
- **Still needed**: sitemap.xml, robots.txt, JSON-LD schema (see README for templates)

### Blog Structure
- Blog posts are in `blog.html` (article preview cards)
- Future: Replace placeholders with actual Italian content (~500 words per article)
- Publishing cadence: 1-2 articles/month recommended (per README)

## Common Maintenance Tasks

### Updating Business Info
Search for + replace across ALL files:
- `+39 XXX XXX XXXX` → actual phone
- `XXXXXXXXXXX` → P.IVA
- `buildminds@pec.it` → real PEC email
- `info@buildminds.it` → real contact email
- LinkedIn URL in footer

### Adding New Pages
1. Copy structure from `index.html` (header, footer, nav)
2. Mark new page as active in nav: `<a href="newpage.html" class="active">`
3. Add link to ALL existing page navs
4. Add footer link (Azienda or Servizi section as appropriate)
5. Create unique title/meta description
6. Follow color scheme from style.css

### Fixing Responsive Issues
- All breakpoint CSS is at bottom of `style.css` under `@media (max-width: 768px)`
- Test via browser DevTools mobile view (375px, 768px, 1024px widths)
- Grid layouts use `repeat(auto-fit, minmax())` - no hardcoded breakpoints needed

## Anti-Patterns to Avoid
- ❌ Adding inline styles - use CSS classes instead
- ❌ Hardcoding colors - always use CSS variables (`var(--primary-color)`, etc.)
- ❌ Using `<div>` for layout without semantic meaning - prefer `<section>`, `<article>`, `<header>`, `<footer>`
- ❌ JavaScript frameworks or build tools - keep it plain HTML/CSS/vanilla JS
- ❌ External icon libraries - use emoji instead (per existing pattern: 💻, 🔧, 📚, 🚀)
- ❌ Changing language to English without updating all pages consistently

## Testing Checklist for Changes
1. ✅ Test on mobile (375px), tablet (768px), desktop (1200px+)
2. ✅ Verify all nav links work (especially new anchors with `id`)
3. ✅ Check CSS colors against design system (primary, secondary, accent, text colors)
4. ✅ Confirm form fields still functional (no broken input IDs)
5. ✅ Update footer links if adding/removing pages
6. ✅ SEO: Update title + meta description for new/changed pages
7. ✅ Validate HTML with W3C validator (no unclosed tags)

---

**Last Updated:** January 2026 | **Deployment:** Netlify/Vercel (static hosting)
