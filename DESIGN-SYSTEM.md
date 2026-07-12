# DESIGN-SYSTEM.md — christaburger.com
*A modern editorial house with a private brass observatory inside it.*

The page is the editorial house: paper, ink, air, and rule lines — spacious, confident, readable. The observatory — plum, midnight, brass — appears in deliberate rooms: the hero, the Quest Layer world, quote panels, the footer. Brown/bronze/gold are accents and live inside the Quest Layer artwork; they never become the page atmosphere.

## 1. Color Tokens

```css
--paper:        #F8F6F1;  /* page background */
--surface:      #FFFFFF;  /* cards, forms, raised surfaces */
--ink:          #192230;  /* headings, body emphasis */
--plum:         #4C365C;  /* primary brand accent, links, buttons */
--midnight:     #22364D;  /* observatory rooms: hero, footer, quote panels */
--forest:       #3F5C50;  /* secondary accent: household/leadership notes */
--antique-gold: #A9854E;  /* brass: eyebrows on dark, fine rules, marks */
--rule:         #DED8CE;  /* hairlines, borders, dividers */
--muted-text:   #66636A;  /* meta text, captions (large/secondary only) */
```

Derived (defined in CSS, not new brand colors):
- `--ink-soft: #333D4D` — body text on paper (AA at 16px+)
- `--plum-deep: #3A2947` — button hover, dark-room gradient partner
- `--gold-bright: #C9A96B` — brass on dark backgrounds (AA on midnight/plum for 14px+ caps text)
- `--paper-dim: #F1EDE4` — alternate band background

**Contrast rules (WCAG AA):** body text = `--ink-soft` or `--ink` on paper/surface. `--muted-text` only ≥0.85rem meta text (4.6:1 on paper). `--antique-gold` on paper only for ≥18px bold or decorative marks — never body copy; small brass labels on light backgrounds use `--plum`. On midnight/plum, text is `#F4F1EA` (near-paper) or `--gold-bright` for labels.

**Legacy aliases:** old template variables (`--blackberry`, `--gold`, `--parchment`, `--stone`, etc.) are remapped to the new tokens in `:root` so untouched templates inherit the new palette automatically.

## 2. Typography

- **Headings & article titles:** Newsreader (opsz axis; 400/500 weights, real italics)
- **Body & interface:** Source Sans 3 (400/600)
- Loaded via `<link>` in head (preconnect + single stylesheet request), `font-display: swap`.

| Role | Font | Size | Notes |
|---|---|---|---|
| Display / hero H1 | Newsreader 500 | clamp(2.6rem–4.2rem) | line-height 1.08, -0.01em |
| H2 | Newsreader 500 | clamp(1.75rem–2.5rem) | line-height 1.15 |
| H3 | Newsreader 500 | clamp(1.3rem–1.6rem) | |
| Article body | Source Sans 3 | 1.1875rem (19px) desktop, 17px mobile | line-height 1.65, max-width 720px |
| UI/body default | Source Sans 3 | 1.0625rem (17px) | line-height 1.6 |
| Eyebrow / label | Source Sans 3 600 | 0.78rem, letter-spacing .18em, uppercase | |
| Meta (dates, reading time) | Source Sans 3 | 0.85rem, `--muted-text` | |
| Pull quote | Newsreader italic | 1.5rem | brass rule top+bottom |

## 3. Spacing & Layout

- Scale: 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 96 / 128 px (`--space-1..-10`).
- Containers: `--container: 1120px` (site), `--container-narrow: 720px` (article column), `--container-wide: 1280px` (rare).
- Section rhythm: `--section-pad: clamp(4rem, 8vw, 6.5rem)` vertical.
- Rules, not boxes: prefer 1px `--rule` hairlines and generous whitespace over cards. Where cards exist, radius is 2px (no pill cards), border 1px `--rule`, shadow only on hover and subtle.

## 4. Components

- **Buttons** (`.btn`): rectangular, 2px radius, 0.8rem/600/caps-spaced label.
  - `.btn--primary`: plum fill, paper text; hover plum-deep.
  - `.btn--brass`: antique-gold fill, ink text — reserved for dark rooms.
  - `.btn--quiet`: 1px ink outline on light / paper outline on dark.
- **Eyebrow** (`.eyebrow`): plum on light, gold-bright on dark.
- **Rule divider** (`.rule`): 48px 1px brass hairline with center diamond ◆ option.
- **Article card** (`.card-essay`): hairline-framed, small landscape thumbnail (16:9 crop, 44% saturation-tempered) or a typographic category plate (no image walls); category label, title, one-line lead, meta row (date · reading time · series glyph ✦).
- **Category plate** (`.plate--governance/quest/household/leadership`): typographic tile in midnight/plum/forest/paper-dim respectively with brass category mark — used when a restrained thumbnail is unavailable or on dense grids.
- **Pull quote** (`.pull-quote`): Newsreader italic 1.5rem, brass hairlines above/below, plum text.
- **Figure** (`.figure` / styled `figure`): full-column image, caption 0.85rem muted, top rule.
- **Quote panel** (`.quote-panel`): midnight room, Newsreader italic, gold-bright emphasis.
- **Author block** (`.author-block`): headshot 64px, name Newsreader, one-line bio, hairline frame.
- **Newsletter block** (`.letters`): "Letters from the Desk" — paper-dim band, single email field + button, one-line promise.
- **Forms**: surface inputs, 1px rule border, plum focus ring (2px, visible), labels always visible.
- **Header**: sticky, paper with hairline bottom rule (not dark). Name in Newsreader. Five top items; Ideas and Work are accessible disclosure dropdowns (button + `aria-expanded`, keyboard and touch friendly). Mobile: hamburger → full-width panel.
- **Footer**: midnight room. Positioning statement, newsletter, nav columns, copyright, privacy + accessibility links.

## 5. Idea-World Accents

Each editorial world carries a discreet accent used in its category plate, landing page eyebrow, and series glyph — never full-page tinting:
- Governance & AI → midnight
- Quest Layer → plum + brass (the observatory itself; full bronze artwork stays inside articles)
- Automated Household → forest
- Leadership & Aliveness → paper-dim + plum

## 6. Motion & Access

- Transitions ≤250ms, opacity/transform only. All motion, smooth-scroll, and the hero video pause under `prefers-reduced-motion: reduce` (video also gets `poster` fallback).
- Focus visible everywhere (`:focus-visible` 2px plum outline, 2px offset).
- Semantic landmarks: `header/nav/main/footer`, one `h1` per page, skip-link.
- Images: `loading="lazy"` (below fold), explicit `width/height` or `aspect-ratio` to prevent CLS, meaningful alt text.

## 7. Anti-goals

No sepia page atmosphere. No gradient blobs. No glassmorphism. No rounded-card fields. No dark-purple full-site theme (the observatory is visited, not lived in). No uppercase body text. No text-only-in-images.
