# CONTENT-INVENTORY.md — christaburger.com
*All approved copy is preserved verbatim. This inventory records what exists, its metadata state, and the (metadata-only) curation applied in the redesign.*

## Pages

| URL | Source | Layout | Status |
|---|---|---|---|
| `/` | theme index.html | home | Rebuilt to new section order (copy preserved) |
| `/about/` | content/about.md | about | Copy in template; restyled, shell shared |
| `/book/` | content/book.md | book | Kept; restyled |
| `/contact/` | content/contact.md | contact | Kept; Netlify form preserved |
| `/work-with-me/` | content/work-with-me.md | work | Kept ("Governance & Advisory") |
| `/speaking/` | content/speaking.md | speaking | Kept ("Speaking & Workshops") |
| `/leadership-work-life/` | content/leadership-work-life.md | prose | Kept |
| `/media-kit/` | content/media-kit.md | prose | Kept |
| `/vault/` | content/vault.md | downloads | Kept, noindex |
| `/automated-household/` (+ stable-system, build-your-own, downloads) | section | household/prose/gate | Kept |
| `/blog/` | section | blog/list | Rebuilt as editorial library |
| `/field-notes/` | **new** | prose/field-notes | Future premium offering — waitlist only |
| `/privacy/` | **new** | prose | Required footer link |
| `/accessibility/` | **new** | prose | Required footer link |

## Editorial categories (new, replacing "Practical AI")

Category landing pages at `/categories/<slug>/`: **Governance & AI**, **Quest Layer**, **Automated Household**, **Leadership & Aliveness**. `/categories/practical-ai/` → redirect to `/blog/`.

## Series

- **Things I've Learned Experimenting With AI** — 29 posts (Apr 20 – Jun 24)
- **The Quest Guide Era** — 7 posts (normalized: the enterprise-software post's long series name folded in; old series URL redirected)

## Post inventory & category mapping

| Slug | Date | New category | Flags |
|---|---|---|---|
| speaking-about-ai-without-the-hype | 03-10 | Governance & AI | needs description ✔ added |
| what-ai-governance-actually-means | 03-28 | Governance & AI | Essential, Start Here; description added |
| the-ai-moment-is-now | 04-16 | Governance & AI | description added |
| the-problem-with-one-giant-ai-assistant | 04-20 | Governance & AI | Start Here |
| when-to-use-broad-ai-prompts | 04-22 | Governance & AI | |
| metaphor-as-ai-architecture | 04-24 | Quest Layer | Essential |
| ai-should-prepare-decisions-not-replace-judgment | 04-27 | Governance & AI | Essential |
| human-in-the-loop-is-not-enough | 04-29 | Governance & AI | |
| the-task-is-never-the-task | 05-01 | Automated Household | |
| small-ai-requests-repeatable-workflows | 05-04 | Governance & AI | |
| recurring-work-pretending-to-be-one-off | 05-06 | Automated Household | |
| heroics-are-a-design-problem | 05-08 | Leadership & Aliveness | Essential |
| set-it-and-forget-it-ai-automation | 05-11 | Governance & AI | |
| reminders-are-not-systems | 05-13 | Automated Household | Start Here |
| i-think-we-talked-about-this-is-not-a-control | 05-15 | Governance & AI | |
| accountability-should-not-require-archaeology | 05-18 | Governance & AI | |
| ai-and-the-work-before-the-work | 05-20 | Automated Household | |
| invisible-work-is-still-work | 05-22 | Automated Household | Essential, Start Here |
| ai-should-protect-aliveness | 05-25 | Leadership & Aliveness | Essential, Start Here |
| automation-should-not-eat-the-human | 05-27 | Leadership & Aliveness | |
| margin-is-the-metric-for-useful-ai | 05-29 | Leadership & Aliveness | |
| not-every-ai-should-be-the-same-ai | 06-01 | Governance & AI | |
| give-ai-a-job-description-before-access | 06-03 | Governance & AI | |
| ai-ecosystems-beat-ai-assistants | 06-05 | Governance & AI | |
| unnamed-work-becomes-weather | 06-08 | Automated Household | |
| good-ai-should-leave-something-usable | 06-10 | Governance & AI | |
| chat-is-the-workshop-not-the-warehouse | 06-12 | Governance & AI | |
| turn-ai-output-into-infrastructure | 06-15 | Governance & AI | |
| ai-productivity-is-too-vague | 06-17 | Governance & AI | |
| ai-loves-a-pancake | 06-19 | Automated Household | |
| prompting-is-not-the-endgame | 06-22 | Governance & AI | |
| my-ai-maturity-ladder-chat-to-choreography | 06-24 | Governance & AI | |
| smaller-lives-four-burners | 07-06 | Leadership & Aliveness | |
| quest-guide-on-a-quest | 07-06 | Quest Layer | series pt 1 |
| quest-guide-dashboard | 07-06 | Quest Layer | series pt 2 |
| quest-guide-alignment | 07-06 | Quest Layer | series pt 3 |
| quest-guide-control-tower | 07-06 | Quest Layer | series pt 4 |
| quest-guide-quest-layer | 07-06 | Quest Layer | Essential; series pt 5 |
| the-future-of-enterprise-software-quest-layer | 07-07 | Quest Layer | series fix (name normalized) |
| quest-guide-how-it-works | 07-07 | Quest Layer | series pt 6 (bonus) |

**Start Here** (4): invisible-work-is-still-work · the-problem-with-one-giant-ai-assistant · what-ai-governance-actually-means · ai-should-protect-aliveness · reminders-are-not-systems *(5 candidates; template shows 4)*
**Essential Essays** (flag `featured: true`): what-ai-governance-actually-means · invisible-work-is-still-work · ai-should-protect-aliveness · quest-guide-quest-layer · heroics-are-a-design-problem · metaphor-as-ai-architecture

## Article data model (added fields, all optional)

```yaml
access: public          # public | email | member — default public; nothing gated today
featured: true          # Essential Essays collection
start_here: true        # Start Here section
description: "…"        # now present on all 40 posts
image_alt: "…"          # backfilled where missing (descriptive, factual)
```

## Assets

- 49 static files; hero video `lavender-night.mp4` (+poster); Quest Layer bronze artwork (6), pony portraits (9), photography (florals/water/landscape), headshots (3), 5 vault PDFs in `static/downloads/`.
- Full Quest Layer artwork remains inside articles; archive cards use tempered thumbnails/category plates per DESIGN-SYSTEM §4.

## Not changed

All body copy of every post and page. Mailchimp form/action/tags. Netlify contact form. GoatCounter. Vault gating flow. Book launch-team flow. Title policy (VP of Cybersecurity).
