# Kai — Publishing Instructions & Workflow Guide

*Maintained by Caleb. Update this file whenever Kai's actual cron prompt changes, so it never drifts from what she really does. Last written: September 12, 2026.*

This covers one lane of Kai's work: publishing to christaburger.com. Kai is Christa's Hermes agent — full name Kairos Arkura, named April 6, 2026 ("she prayed over it"). Beyond this site, she also runs the WatchTok Discord crons (Word/Kaomoji of the Day, daily digest, welcome, events) and the Hall of Echoes / LiDAR archaeology work. This document is scoped to publishing only.

## How publishing works today (the live pipeline)

Nothing about this is manual on Kai's end — it's a daily cron, not a chat conversation:

1. **Trigger.** Christa emails **christaha27@gmail.com**, from herself, with **"blog" in the subject line**. Body must be **500+ characters** or the prefetch script ignores it (treated as a quick note, not a post).
2. **Pickup.** Every morning at **8:00am MT**, a Hermes cron (`Blog Email Deploy`, job id `a79d0b12aff6`) runs `blog_prefetch.py`, which logs into that inbox via IMAP, searches the last 30 days for matching emails, strips quoted reply chains, and skips anything already deployed (tracked in `~/.hermes/scripts/blog_deployed.json`).
3. **Parse.** For each new post: title = first line of the body, slug = lowercased/hyphenated title (ASCII only, no apostrophes, max 50 chars), lead = second line or a one-sentence summary Kai writes, date = the day it's deployed (today, never future-dated).
4. **Image.** If the email has an image attachment, Kai uses it — copied to `~/christaburger/themes/christa/static/images/[slug].jpg`. **If there's no attachment, she falls back to an Unsplash URL matched to the post's mood.** (See open decision #1 below — this doesn't yet pull from your local image folder.)
5. **Write.** Kai writes `~/christaburger/content/blog/[slug].md` with Hugo frontmatter (title, slug, date, lead, description, image, image_alt, tags, series if applicable) followed by the body **verbatim** — she's instructed never to rewrite or summarize your words.
6. **Build & ship.** `cd ~/christaburger && hugo --minify`, then `git add -A && git commit -m "Add post: [Title]" && git push`.
7. **Report.** Kai lists each deployed post with its live URL.

The site itself is a **Hugo static site in `~/christaburger`, deployed via git push** — not Ghost/Casper. (Your notes from earlier this year say Ghost — flagging that in case the platform changed underneath without the notes catching up, or in case there's a second site I haven't found. Worth a quick confirm from you.)

## How to publish a post, in practice

Just email it to yourself: subject with "blog" in it, body starting with the title on line one, the lead/summary on line two, full post text after that, image attached if you have one. Kai picks it up the next morning at 8am — there's no faster path unless someone runs the cron manually.

## Where Kai's actual instructions live

Not in a "global instructions" file the way Caleb has one — Kai's publishing behavior is the **prompt text inside the cron job itself**: `~/.hermes/cron/jobs.json`, job `"Blog Email Deploy"` (`id: a79d0b12aff6`). That prompt *is* her governing instructions for this task, run fresh each morning. Editing it changes what she does in production the very next run — treat it like editing live code, not like a casual note.

**Convention going forward:** Caleb drafts any proposed change to that prompt and shows it to Christa before it goes live, unless Christa says to just make the edit directly.

## Open decisions (before the Formation Governance series runs)

You mentioned wanting the ten Sophia-drafted posts to go out with dispersed publish dates and a feature image pulled from `.../Personal Website/Website-artifacts/Images` on each one. The pipeline as it exists today doesn't quite do either automatically:

1. **Feature images.** Kai only overrides the Unsplash fallback when an email has an attachment. To pull from your image folder instead, pick one:
   - Attach the image you want to each blog email yourself (zero code change, works today).
   - Have Caleb add a step where Kai looks in that folder and picks an image (by filename match, by "next unused," or some other rule you specify).
2. **Dispersed dates.** Each post is dated the day it's emailed, and Hugo hides future-dated posts by default (`hugo --minify` doesn't build them unless run with `--buildFuture`). To spread ten posts over time, pick one:
   - Send the ten emails on ten different real days — simplest, no code change, but means you're the scheduler.
   - Have Caleb add future-dating + a `--buildFuture` build step so all ten can be queued in one batch and Kai releases them on a schedule you set.

Neither of these breaks anything today — they just mean the series will publish exactly as fast as you email it, all dated the day it lands, with Unsplash images unless you attach your own. Let me know which way you want to go on each and I'll draft the cron prompt change for your review.

## Division of labor

- **Kai** — christaburger.com publishing, WatchTok Discord operations, Hall of Echoes / LiDAR archaeology work.
- **Caleb** — drafts and maintains this document and proposed changes to Kai's cron prompt; doesn't edit her live instructions without Christa's sign-off; everything else across the household/ventures/finances lanes.
- **Thom** — deep thinking and formation work, in the Claude.ai chat interface.

## Reference — the live cron prompt, verbatim (as of Sep 12, 2026)

```
You are Kai, Christa's deploy agent for christaburger.com.

The prefetch script has checked christaha27@gmail.com for new blog emails from Christa. The results are injected above.

If status is "nothing_new" — respond with [SILENT] and stop.

If status is "new_posts" — deploy each post to christaburger.com using this exact workflow for EACH post:

STEP 1 — Parse the post
- Title: first line of the body (strip series labels like "(1 of 5...)" if present)
- Slug: lowercase title, hyphens only, no apostrophes or special chars, max 50 chars
- Lead: second non-empty line or a one-sentence summary you write
- Series tag: if body mentions "in this series" or has a series name, extract it
- Body: full body text verbatim (it is Christa's writing — do not rewrite or summarize)
- Date: today's date in YYYY-MM-DD format

STEP 2 — Pick image
- If attachments exist: use the first image attachment. Copy it to ~/christaburger/themes/christa/static/images/[slug].jpg using python subprocess or os.system
- If no attachments: use an Unsplash URL that matches the post mood

STEP 3 — Write the markdown file
Path: ~/christaburger/content/blog/[slug].md
Frontmatter format (use double-quotes, no apostrophes in YAML values):
---
title: "Title Here"
slug: slug-here
date: 'YYYY-MM-DD'
lead: One sentence lead here.
description: Two sentence description for SEO.
image: /images/[slug].jpg
image_alt: Brief image description
tags:
- AI strategy
- Leadership
series: "Series Name"
---

Then the full post body verbatim.

STEP 4 — Build and push
Run these commands via Python subprocess:
1. cd ~/christaburger && hugo --minify
2. Verify public/blog/[slug]/ exists
3. git add -A
4. git commit -m "Add post: [Title]"
5. git push

STEP 5 — Update the deployed log
Read ~/.hermes/scripts/blog_deployed.json, add the email_id to deployed_ids array, write it back.

STEP 6 — Report back
List each post deployed with its URL: christaburger.com/blog/[slug]

CRITICAL RULES:
- Never use apostrophes in filenames or slugs — use plain ASCII only
- Date must be today or earlier — never future-date a post
- Do NOT rewrite Christa's content — deploy verbatim
- Use Python urllib for all file operations, subprocess for shell commands
- If a post fails to build, skip it and report the error — do not block other posts
```
