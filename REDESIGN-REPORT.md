# REDESIGN-REPORT.md — christaburger.com
*Completed July 11, 2026 · branch `redesign/editorial-house` (main untouched, nothing deployed)*

## 1. Summary of changes

The site moved from a dark blackberry-and-gold theme to **the editorial house with a brass observatory inside it**: paper-first pages set in Newsreader + Source Sans 3, with plum/midnight/forest accents and brass reserved for fine rules, marks, and the dark rooms (hero, quote panels, series banners, footer). Every word of approved copy is preserved — the work was design, architecture, metadata, and conversion.

**Information architecture.** Nine flat nav items became five: Ideas (All Writing, Quest Layer, Automated Household, Leadership, AI & Governance), Work (Governance & Advisory, Speaking, Workshops), Book, About, Contact — with accessible disclosure dropdowns (keyboard, Escape, click-outside all tested). One shared footer everywhere: positioning statement, newsletter signup, primary nav, copyright, privacy/accessibility/RSS links.

**Home** rebuilt in the mandated order: hero (with "Explore the Ideas" / "Work With Christa" CTAs), credibility strip, three idea worlds, six curated essential essays, book feature, advisory & speaking, Letters from the Desk, closing CTA.

**Writing system.** The chronological wall became an editorial library: Start Here (4 essays), Browse by World (4 category tiles), Essential Essays, two series banners, then all 40 essays with category labels, reading time, dates, series indicators, and restrained thumbnails (tempered crops or typographic category plates — no bronze wall). Four category landing pages with curated intros replace the single "Practical AI" bucket; every post was re-categorized. The mismatched Quest Guide series name was normalized (one series page instead of two).

**Article template** is now premium long-form: category, title, subtitle, date, reading time, series note, featured image with caption support, 720px/19px/1.65 reading column, pull-quote styling, mobile-safe tables (scroll-wrapped via render hook), share row, author block, series prev/next, related reading, older/newer navigation, newsletter CTA, and Article JSON-LD.

**Premium-ready model.** Every post now carries `access: public` (model supports `email` and `member`; badge rendering built into the template). `/field-notes/` is a polished waitlist-only landing page explaining the future offering — no paywall, no payment vendor, nothing existing gated. `/membership` redirects there.

**SEO.** Canonical URLs, unique titles/descriptions on every page, OpenGraph + Twitter cards with image fallback, Person/WebSite/Article structured data, robots.txt, RSS advertised in head, per-category RSS feeds, and 301 redirects for the two retired URLs.

## 2. Files changed

**New:** `SITE-AUDIT.md`, `DESIGN-SYSTEM.md`, `CONTENT-INVENTORY.md`, `REDESIGN-REPORT.md`, `.gitignore`, `content/field-notes.md`, `content/privacy.md`, `content/accessibility.md`, `content/blog/_index.md`, `content/categories/*/_index.md` (×4), `content/series/*/_index.md` (×2), `themes/christa/layouts/partials/card-essay.html`, `themes/christa/layouts/_default/field-notes.html`, `themes/christa/layouts/_default/_markup/render-table.html`.

**Rewritten:** `themes/christa/static/css/main.css` (full design system, legacy variable aliases keep older templates coherent), `partials/head.html`, `partials/nav.html`, `partials/footer.html`, `layouts/index.html`, `layouts/blog/list.html`, `layouts/blog/single.html`, `layouts/_default/term.html`, `archetypes/default.md`.

**Edited:** `hugo.yaml` (menu, outputs incl. category RSS, robots, related), `netlify.toml` (redirects), `content/book.md` + `content/automated-household/downloads.md` (meta_title only), all 40 `content/blog/*.md` (front matter only: categories, series normalization, access, featured/start_here flags, missing descriptions/alt text), small accessibility/lazy-loading touch-ups in `_default/{single,speaking,prose,about,book,household,contact,gate,downloads}.html`.

**Removed from git:** `public/` (build artifact; Netlify builds from source).

## 3. Remaining known issues

- The "Living Proof" home band (water lilies + "smallest complete governance environment" copy) was retired to follow the mandated home structure; the same story is told on /book and /automated-household. Easy to restore as a section 6½ if you miss it.
- Font files load from Google Fonts (network dependency); self-hosting would improve performance and privacy — deferred.
- Vault PDFs are slide-deck exports and not fully screen-reader friendly (noted on /accessibility/).
- The email/member access tiers render a badge but no actual gate — intentional until a membership backend exists.
- Lighthouse was not run (no Chrome DevTools in the sandbox); axe-core WCAG 2.1 A/AA scans across 21 representative pages returned **0 violations**, and manual keyboard/reduced-motion checks passed. Run Lighthouse in Chrome after deploy for the performance score.

## 4. Deployment instructions

1. Review the branch: `git checkout redesign/editorial-house`, then `hugo server` and click around locally.
2. Netlify deploy preview (recommended): push the branch — `git push origin redesign/editorial-house` — and open the Netlify deploy preview to verify forms (Netlify Forms detection re-runs per deploy) and the Mailchimp signup.
3. Ship: merge to the production branch (`git checkout main && git merge redesign/editorial-house && git push`). Netlify builds with `hugo --minify` / Hugo 0.160.1 — unchanged.
4. Post-deploy: submit the contact form once as a test; confirm `/categories/practical-ai/` and the long Quest Guide series URL both 301; spot-check `/sitemap.xml` and a category RSS feed (`/categories/quest-layer/index.xml`).

## 5. Screenshots

In the session outputs folder (`screenshots/`): before/after home at 1440/1024/768/390, before/after library and article at 1440 + 390, plus after-category, after-field-notes, after-about, and the mobile menu open state.

## 6. Recommendations intentionally deferred

- **Self-host fonts** (performance + privacy).
- **LinkedIn/TikTok links in the footer** — no social profiles are configured on the site today; add when you want them public.
- **Newsletter provider page for "Letters from the Desk" archive** — past letters aren't on the site; a /letters/ archive would be a natural next room.
- **Image pipeline** — Hugo image processing (responsive srcset, WebP) would cut page weight meaningfully; needs images moved from `static/` to `assets/`.
- **Search** — 40+ essays is the threshold where a small client-side search (Pagefind) starts earning its keep.
- **Stripe/Memberful integration for Field Notes** — the content model and landing page are ready; wire a provider only when the offering is real.
- **OG image generation** — per-essay social cards in the brand system (currently falls back to essay art or headshot).
