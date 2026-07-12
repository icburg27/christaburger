# SITE-AUDIT.md — christaburger.com
*Audit date: July 11, 2026 · Auditor: Caleb (pre-redesign inspection)*

## Framework & Build

- **Generator:** Hugo 0.160.1 (extended), custom theme `themes/christa`. No page bundles; flat markdown under `content/`.
- **Build:** `hugo --minify` via Netlify (`netlify.toml`, `HUGO_VERSION=0.160.1`, publish dir `public`).
- **Hosting:** Netlify. Contact form uses Netlify Forms (`data-netlify="true"`). Newsletter uses Mailchimp JSONP (list `u=224f7efe…&id=92488633b9`) via `partials/mc-form.html`.
- **Analytics:** GoatCounter (`christaburgerwebsite.goatcounter.com`), loaded in `head.html`.
- **Repo quirk:** `public/` (built output) is committed to git. Netlify rebuilds from source, so this is dead weight and drifts from source. Recommend gitignoring.
- **No CMS** — content is markdown + front matter, edited directly. `brand/` holds strategy docs (voice guide, gold pass, launch strategy) that are not published.

## Content Structure

- 40 blog posts in `content/blog/` (Mar 10 – Jul 7, 2026).
- Section: `content/automated-household/` (4 pages: index, stable-system, build-your-own, downloads gate).
- Single pages: about, book, contact, work-with-me, speaking, leadership-work-life, media-kit, vault (noindex, post-signup).
- Taxonomies: tags (~80 terms), categories (only "Practical AI", used on 32 posts), series (2).

## Template Inventory (themes/christa/layouts)

| Template | Role | Notes |
|---|---|---|
| `index.html` | Home | Good bones; section order differs from target; book/card markup uses heavy inline styles |
| `blog/list.html` | Archive | Pure chronological grid; hardcoded banner for one series only |
| `blog/single.html` | Article | No reading time, no share, no author block, no prev/next, no structured data |
| `_default/single.html` | Fallback | Eyebrow shows raw section name; nearly unused |
| `_default/prose.html` | Generic page | Used by leadership, media-kit, stable-system, build-your-own |
| `_default/about/book/contact/work/speaking/household/gate/downloads.html` | Bespoke pages | Consistent shells (shared nav/footer partials) but heavy inline styling |
| `_default/term.html`, `terms.html` | Taxonomy | Basic; no category intros |

**Good news:** there is exactly ONE header (`partials/nav.html`) and ONE footer (`partials/footer.html`) — no duplicated shells or legacy generations of the site. Inconsistency lives in (a) inline styles scattered through templates, (b) metadata gaps, (c) IA.

## Issues Found

### Information architecture
1. **9 flat top-nav items** (Home, Book, About, Governance, Speaking, Leadership, Household, Writing, Contact) — over target, no grouping, wraps at laptop widths.
2. Footer is nav-only: no positioning statement, no newsletter, no privacy/accessibility links (pages don't exist).
3. Blog is a single chronological wall — no category landing pages, no Start Here, no curation.

### Metadata & taxonomy
4. **Series name mismatch:** `the-future-of-enterprise-software-quest-layer.md` uses series `"The Quest Guide Era: Why Enterprise Work Needs More Than Dashboards"`; the other five use `"The Quest Guide Era"` → generates two series pages for one series.
5. **Category monoculture:** every categorized post is "Practical AI" (32 posts); 7 Quest Guide posts + `smaller-lives-four-burners` have no category at all.
6. 3 posts missing `description:` (speaking-about-ai-without-the-hype, the-ai-moment-is-now, what-ai-governance-actually-means).
7. Most posts missing `image_alt` (only the Quest Guide era posts have it).

### SEO / distribution
8. `head.html` missing: canonical URL, `og:type`, `og:url`, Twitter card tags, RSS `<link>`, structured data (no Article/Person/WebSite JSON-LD anywhere), favicon.
9. `og:title` uses bare `.Title` even on home (no site suffix); home `<title>` fine.
10. Sitemap ✓ and RSS ✓ (Hugo defaults) — but not advertised in `<head>`. Category feeds exist per Hugo defaults once categories are real.
11. No social-share image fallback when a post lacks `image`.

### Design / CSS
12. Palette is "Blackberry & Gold on Parchment" (deep purple #241634/#34224A + gold #C8994C) — dark, theatrical; nav and multiple full bleed dark bands. Target palette is paper-first editorial.
13. Fonts: Fraunces + Inter via CSS `@import` (render-blocking inside stylesheet; should be `<link>` with preconnect — preconnects exist in head but the @import defeats them).
14. Body text 16px / #3E3A44 on white at 1100px-wide grid; article column `container--narrow` is 760px with 1.05rem text — below the 18–20px / 720px editorial target.
15. Heavy inline styles throughout templates (book card, CTAs, section paddings) — inconsistent spacing scale.
16. No `prefers-reduced-motion` handling (hero autoplay video, hover transforms, smooth-scroll).
17. No lazy loading on images; no width/height attributes → layout shift on archive grids.
18. Contrast concerns: `--text-light: #8A8194` on white (~3.7:1) used for small text; gold #C8994C on parchment for small labels (~2.4:1) — WCAG AA failures in places.
19. Mobile nav toggle exists and works; dropdown IA will need new accessible disclosure pattern.

### Stale / drift
20. `hugo.yaml` `subtagline: "Build systems people can trust."` unused; voice guide says it was meant as homepage H1 — superseded by "You were never meant to be the system." No action needed beyond noting.
21. Title policy (brand/voice-guide.md, July 2026): public credential is **VP of Cybersecurity**; site complies. Employer not named — complies.
22. `content/vault.md` is `noindex` gated deliverable page — correct, keep.
23. No privacy policy or accessibility statement pages exist (required by new footer).
24. No social profiles configured anywhere on the site (brief: include "if currently configured" → omit; recommend adding LinkedIn later).

## URL Inventory (must all keep resolving)

Pages: `/`, `/about/`, `/book/`, `/contact/`, `/work-with-me/`, `/speaking/`, `/leadership-work-life/`, `/media-kit/`, `/vault/`, `/automated-household/`, `/automated-household/stable-system/`, `/automated-household/build-your-own/`, `/automated-household/downloads/`, `/blog/`, 40 × `/blog/<slug>/`, `/tags/*`, `/categories/practical-ai/`, `/series/things-ive-learned-experimenting-with-ai/`, `/series/the-quest-guide-era/`, `/series/the-quest-guide-era-why-enterprise-work-needs-more-than-dashboards/` (duplicate to be redirected), `/index.xml`, `/sitemap.xml`, plus static `/downloads/*.pdf`, `/images/*`, `/videos/*`.

Redirects required after refactor:
- `/categories/practical-ai/` → `/blog/` (category retired in favor of four editorial categories)
- `/series/the-quest-guide-era-why-enterprise-work-needs-more-than-dashboards/` → `/series/the-quest-guide-era/` (series name normalized)

## Baseline Build

`hugo` builds clean: **190 pages, 49 static files, 0 errors** (verified 2026-07-11).
