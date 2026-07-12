# MEDIUM-PUBLISHING-GUIDE.md
*Cross-publishing to Medium while christaburger.com remains the permanent source of truth.*
*Prepared July 2026. Nothing is exported or duplicated in this repo — Medium receives syndicated copies with canonical links pointing home.*

## The principle

christaburger.com is the library. Medium is a reading room in someone else's city. Every essay lives, updates, and ranks at christaburger.com; Medium copies carry a canonical link back home, so search engines credit the original and readers can find the house. If Medium ever changes its rules, delete the copies and nothing of value is lost.

## What the site now provides (verified)

- **Canonical metadata** — every article page declares `rel="canonical"` to its christaburger.com URL.
- **Clean article HTML** — semantic `<article>` markup, real headings, blockquotes, figures, and tables; imports cleanly.
- **OpenGraph images** — every one of the 40 essays has a featured image emitted as `og:image` (site-wide headshot fallback for pages without one).
- **Full-content RSS** — `/index.xml`, `/blog/index.xml`, and per-category feeds now carry complete article HTML (`content:encoded`), the featured image, author (`dc:creator`), publication dates, and category + series metadata. Any import or syndication tool can work from the feed alone.
- **Author metadata** — `meta author`, `article:author`, and Person JSON-LD on every article.
- **Publication dates** — visible on page, in `article:published_time`, JSON-LD, and RSS.
- **Category & series metadata** — `article:section`, `article:tag`, RSS categories, and visible series navigation.
- **Consistent end-of-article block** — every article on the site ends with the author block and the Letters from the Desk invitation; the Medium equivalent is the paste-ready end-block below.

## Recommended import workflow

Medium's **Import a story** tool ([help article](https://help.medium.com/hc/en-us/articles/214550207-Importing-a-post-to-Medium)) is the backbone: it pulls the article from its christaburger.com URL, backdates it to the original publication date, and **sets the canonical link automatically**. Manual stories can also set a canonical via Medium's [canonical link setting](https://help.medium.com/hc/en-us/articles/360033930293-Set-a-canonical-link), but import is the default path.

1. On Medium: profile menu → **Stories** → **Import a story** → paste the essay's christaburger.com URL.
2. Let it import, then edit the draft: fix any figure/caption oddities, restore pull-quote emphasis, confirm the featured image imported (re-upload from /images/ if not).
3. Replace the imported site footer matter (author block / newsletter section, if it came along) with the **Medium end-block** below.
4. Retitle and re-subtitle per the table below — Medium headlines work harder than editorial ones.
5. Add exactly 5 topics (Medium's maximum) from the topic sets below.
6. **Verify the canonical**: the story should show "Originally published at christaburger.com" at the bottom. If it doesn't, set it manually before publishing (once published, canonical cannot be changed on Medium).
7. Publish free (metering strategy below), then add the story link to the tracking table at the bottom of this file.

**Never** paste article text into a fresh Medium story without a canonical link — that creates the duplicate-content problem this whole system exists to prevent.

## Preserving christaburger.com as canonical

- Import (or set canonical manually) — no exceptions, ever.
- Publish on Medium **at least a week after** the essay is live at home, so search engines index the original first.
- Never publish anything on Medium that isn't already on christaburger.com.
- All links inside the Medium copy that point home carry UTM tags so GoatCounter shows the Medium referral clearly:
  `https://christaburger.com/<path>/?utm_source=medium&utm_medium=syndication&utm_campaign=<essay-slug>`
- If an essay is ever revised at home, revise the Medium copy the same day or delete it. The copies are echoes, not siblings.

## The Medium end-block (paste at the end of every story)

> *Originally published at [christaburger.com](https://christaburger.com/?utm_source=medium&utm_medium=syndication&utm_campaign=END-SLUG).*
>
> **Christa Burger** is a cybersecurity governance executive and the author of *The Automated Household* — a field guide to transferring mental load, building household systems, and using AI to make you more human. She builds operating systems for real life, so the system carries the repetition and the humans carry the meaning.
>
> For one good letter every couple of weeks — governance without theater, AI without hype, and the systems that carry a real life — join [Letters from the Desk](https://christaburger.com/blog/?utm_source=medium&utm_medium=syndication&utm_campaign=END-SLUG#letters). The first chapter of the book is [free](https://christaburger.com/book/?utm_source=medium&utm_medium=syndication&utm_campaign=END-SLUG).

Replace `END-SLUG` with the essay's slug each time.

## The five launch essays

Sequenced roughly one per week — a debut month, not a dump. Lead with the Quest Layer flagship (most distinctive, most shareable), establish the governance credential second, then widen to the household and leadership audiences.

| # | Essay (canonical URL slug) | Medium title | Medium subtitle | Topics (5) | End CTA emphasis |
|---|---|---|---|---|---|
| 1 | `quest-guide-quest-layer` — The Future of Enterprise Software May Be in the Quest Layer | The Future of Enterprise Software Is a Quest Layer | We're no longer limited to the software categories vendors hand us. We can build interfaces around how work actually works. | Future Of Work, Enterprise Software, Artificial Intelligence, Product Management, Leadership | Letters from the Desk + the series link home |
| 2 | `quest-guide-alignment` — Corporate Work Is Already a Quest. We Just Keep Calling It Alignment. | Corporate Work Is Already a Quest. We Just Keep Calling It Alignment. | Alignment answers whether we're facing the same mountain. A quest guide helps us climb it. | Leadership, Management, Future Of Work, Workplace Culture, Strategy | Series link home + Letters |
| 3 | `what-ai-governance-actually-means` — What AI Governance Actually Means (And Why Most Organizations Get It Wrong) | Most Organizations Aren't Governing AI. They're Hoping Policies Behave Like Systems. | Real AI governance answers three questions: who decides, what values guide it, and how it evolves. | AI Governance, Artificial Intelligence, Leadership, Technology, Risk Management | Governance & Advisory page + Letters |
| 4 | `invisible-work-is-still-work` — Invisible Work Is Still Work, and AI Can Help Reveal It | Remembering Is Work. Noticing Is Work. It's Just Badly Marketed. | The invisible cognition that runs your household is real labor — and AI can finally make it visible enough to share. | Mental Load, Artificial Intelligence, Family, Productivity, Women In Tech | Book free chapter + Letters |
| 5 | `heroics-are-a-design-problem` — Heroics Are Usually a Design Problem | The Late-Night Save Is Not a Virtue. It's a Signal. | A broken system relying on one person's goodwill is still a broken system — at work and at home. | Leadership, Burnout, Systems Thinking, Management, Work Life Balance | Book + Governance & Advisory |

**Second wave candidates** (after the debut month, judged by what resonates): `metaphor-as-ai-architecture`, `ai-should-protect-aliveness`, `quest-guide-how-it-works`, `give-ai-a-job-description-before-access`, `the-problem-with-one-giant-ai-assistant`.

## Free vs. metered

**Stay free (always):** the funnel essays — anything whose job is to bring readers home to the newsletter, the book, or the advisory practice. That's essays 3, 4, and 5 above, everything in Start Here, and anything referenced from the book. A meter between a new reader and the front door defeats the purpose of syndicating.

**Test as metered:** the Quest Layer enterprise essays (1, 2, and later series pieces). Their audience — product and enterprise leaders — lives on Medium, is disproportionately made of members, and the pieces stand alone as ideas rather than as doorways. Test one metered after the free debut month and compare read-through and referral traffic against its free siblings before metering more.

**Caveat to verify at signup:** Partner Program terms change; confirm imported/canonical stories are currently meter-eligible when enrolling. If they're not, everything runs free and the strategy is unaffected — the essays' job on Medium is reach, not revenue.

## Repeatable publication checklist

For every essay syndicated to Medium:

- [ ] Essay has been live on christaburger.com for 7+ days
- [ ] Imported via **Import a story** from the canonical URL (not pasted)
- [ ] "Originally published at christaburger.com" canonical note visible on the draft
- [ ] Title and subtitle set (Medium-tuned, per table or same spirit)
- [ ] Featured image present; figures and pull quotes read cleanly
- [ ] Site footer matter removed; **Medium end-block** pasted with `END-SLUG` replaced
- [ ] All links home carry the UTM convention
- [ ] Exactly 5 topics chosen
- [ ] Free/metered decision made deliberately (default: free)
- [ ] Published; story URL added to the tracking table below
- [ ] A week later: check GoatCounter for `utm_source=medium` campaigns and note reads/claps

## Tracking table

| Date | Essay slug | Medium URL | Free/Metered | Notes |
|---|---|---|---|---|
| | | | | |

## Sources

- [Importing a post to Medium — Medium Help Center](https://help.medium.com/hc/en-us/articles/214550207-Importing-a-post-to-Medium)
- [Set a canonical link — Medium Help Center](https://help.medium.com/hc/en-us/articles/360033930293-Set-a-canonical-link)
- [How to Syndicate and Republish to Medium with Canonical URLs — brianli.com](https://brianli.com/how-to-syndicate-and-republish-to-medium-with-canonical-urls/)
