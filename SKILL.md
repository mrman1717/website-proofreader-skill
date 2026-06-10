---
name: website-proofreader
license: MIT
metadata:
  version: 1.1.1
  date: 2026-06-10
  author: mrman1717
  repository: https://github.com/mrman1717/website-proofreader-skill
description: |
  Proofread and improve website content: spelling and grammar (UK English),
  AI-ism detection and removal, and on-page SEO review. Use this skill whenever
  the user asks to proofread, check, review, edit, polish, or "look over" web
  copy, landing pages, blog posts, product pages, meta descriptions, or any
  website text — even if they only mention one aspect (e.g. just "check the
  grammar" or "is this too AI-sounding?"). Also trigger when the user pastes
  web copy and asks for feedback, uploads a page draft, gives a URL, sitemap,
  or list of pages to check, or mentions SEO for written content.
---

# Website Proofreader

Proofread website content against the brand's tone of voice, UK English conventions, AI-writing-pattern rules, and current on-page SEO best practices. Return either polished copy with a change log or an annotated report, depending on what the user chooses each run.

## Workflow

Follow these steps in order. Do not skip the setup questions in Step 2 — the user wants to choose these every time.

### Step 1: Load the reference files

Read all four reference files before analysing anything:

1. `references/tone-of-voice.md` — brand vocabulary, voice, and banned words
2. `references/proofing-rules-checklist.md` — spelling, grammar, and consistency rules (UK English)
3. `references/ai-isms.md` — AI-generated-writing patterns to detect and remove
4. `references/seo-checklist.md` — on-page SEO checks, organised by depth level

### Step 2: Ask the setup questions

Before analysing, ask (use tappable options if an option-presenting tool is available, otherwise ask in plain text). Only ask the questions that apply — skip any the user has already answered in their request, and skip questions made irrelevant by the chosen mode.

**Question 1 — Mode:**
- **Proofreader only** — spelling/grammar pass + AI-ism pass; no SEO checks
- **SEO checker only** — SEO pass only; no proofing or AI-ism checks
- **Both** — all three passes

**Question 2 — Output format** (skip if mode is SEO-only; SEO-only always produces a report):
- **Polished copy + change log** — rewrite the content and list every change with a reason
- **Annotated report only** — no rewrite; a structured report of issues with suggested fixes

**Question 3 — SEO depth** (skip if mode is proofreader-only):
- **Basics** — title, meta description, headings, links
- **Standard** — basics + keyword usage and readability
- **Full audit** — standard + content structure, image alt text, AI-search visibility

If a target keyword or topic is needed for SEO checks and hasn't been given, ask for it (or infer it from the content and state your assumption).

### Step 3: Get the content

The user can supply content in any of these ways. Identify which applies before proceeding.

**a) A single URL.** Ask whether they want just that page checked, or the whole site crawled from it. (If it's obviously a deep inner page and they asked to "check this page", don't ask — just check it.)

**b) A whole site (main URL + crawl).** Discover pages by trying `/sitemap.xml` first (also check `robots.txt` for a sitemap location); if no sitemap is found, fall back to following internal links from the main page. List the pages found before analysing.

**c) A sitemap (XML or similar).** Parse it and use the URLs it lists.

**d) A list of pages/URLs.** All URLs must belong to one single site (same registrable domain; subdomains of the same site are fine). If the list spans more than one site, reject it and ask the user to resubmit a single-site list.

**e) Pasted or file-based content.** Content pasted in chat, uploaded as .txt, .md, .docx, .pdf, or .html (in Claude.ai, read uploads from `/mnt/user-data/uploads/`), or pointed to as local files when running in Claude Code or similar.

**Multi-page rules (applies to b, c, d):**

- **Page cap:** fetch and analyse at most **10 pages** per batch. If more are found, list them all, process the first 10 (preferring key pages: home, main service/product pages, about, contact), then ask whether to continue with the next batch.
- **Caching:** in an environment with file access (Claude Code or similar), save a local cached copy of each fetched page's content (e.g. under a `.cache/` or temp folder) and work from the cache — this avoids re-fetching on follow-up batches or re-runs. Don't include cached files in any output or package.
- **Result format:** ask the user whether they want **one combined report** (organised by page) or **a separate output per page plus a site-wide summary** of recurring issues.

For HTML (fetched or uploaded), analyse the rendered text but also check the title tag, meta description, heading hierarchy, and image alt attributes if present.

### Step 4: Run the passes for the chosen mode

Run only the passes the chosen mode includes (proofreader-only: passes 1–2; SEO-only: pass 3; both: all). Work through the content in this order, noting every issue with its location (quote a short snippet so the user can find it):

1. **Proofing pass** — apply `proofing-rules-checklist.md`. UK English spelling and conventions are mandatory; flag every US spelling.
2. **AI-ism pass** — apply `ai-isms.md`. Flag patterns, don't just reword silently; the user wants to learn what to avoid.
3. **SEO pass** — apply `seo-checklist.md` at the depth chosen in Step 2 only. Do not run full-audit checks if the user chose basics.

For multi-page jobs, run the passes per page, and also note site-wide patterns (issues recurring across pages) for the summary.

### Step 5: Deliver the output

**If "Polished copy + change log":**

```
# Polished Copy
[the full rewritten content]

# Change Log
## Spelling & grammar
- "[original]" → "[fixed]" — [reason]
## Tone & AI-isms
- "[original]" → "[fixed]" — [pattern name + reason]
## SEO
- [change or recommendation] — [reason]

# Outstanding recommendations
[anything that needs the user's decision, e.g. missing meta description, keyword choice]
```

**If "Annotated report only":**

```
# Proofreading Report
## Summary
[2-3 sentences: overall quality, biggest issues]
## Spelling & grammar (X issues)
[each: snippet, problem, suggested fix]
## AI-isms (X issues)
[each: snippet, pattern name, suggested fix]
## SEO ([depth level], X issues)
[each: what's wrong, why it matters, recommended fix]
```

Omit sections for passes that weren't run (e.g. no SEO section in proofreader-only mode).

For multi-page jobs, deliver in the format chosen in Step 3 (combined report organised by page, or per-page outputs plus a site-wide summary of recurring issues).

For long content (over ~1,500 words, or any multi-page job), save the output as markdown file(s) and share them rather than flooding the chat.

## Principles

- Preserve the author's meaning and structure. Fix problems; don't rewrite for the sake of it.
- The tone-of-voice file wins over generic style preferences. If it conflicts with an AI-ism rule, follow the tone file and note the conflict.
- Be specific in the change log — vague entries like "improved flow" are useless. Name the rule applied.
- If the content is clean in a category, say so briefly rather than inventing issues.
- When the brand tone-of-voice file still contains template placeholders, mention that filling it in will improve results, then proceed with sensible defaults.
