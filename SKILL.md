---
name: website-proofreader
metadata:
  version: 1.0.1
  date: 2026-06-10
description: |
  Proofread and improve website content: spelling and grammar (UK English),
  AI-ism detection and removal, and on-page SEO review. Use this skill whenever
  the user asks to proofread, check, review, edit, polish, or "look over" web
  copy, landing pages, blog posts, product pages, meta descriptions, or any
  website text — even if they only mention one aspect (e.g. just "check the
  grammar" or "is this too AI-sounding?"). Also trigger when the user pastes
  web copy and asks for feedback, uploads a page draft, or mentions SEO for
  written content.
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

### Step 2: Ask the user two setup questions

Before analysing, ask (use tappable options if an option-presenting tool is available, otherwise ask in plain text):

**Question 1 — Output format:**
- **Polished copy + change log** — rewrite the content and list every change with a reason
- **Annotated report only** — no rewrite; a structured report of issues with suggested fixes

**Question 2 — SEO depth:**
- **Basics** — title, meta description, headings, links
- **Standard** — basics + keyword usage and readability
- **Full audit** — standard + content structure, image alt text, AI-search visibility

If the user has already specified these in their request, don't re-ask — use what they said.

If a target keyword or topic is needed for SEO checks and hasn't been given, ask for it (or infer it from the content and state your assumption).

### Step 3: Get the content

Accept content pasted in chat, or uploaded as .txt, .md, .docx, .pdf, or .html. For uploaded files, read them from `/mnt/user-data/uploads/`. For HTML, analyse the rendered text but also check the title tag, meta description, heading hierarchy, and image alt attributes if present.

### Step 4: Run the three passes

Work through the content in this order, noting every issue with its location (quote a short snippet so the user can find it):

1. **Proofing pass** — apply `proofing-rules-checklist.md`. UK English spelling and conventions are mandatory; flag every US spelling.
2. **AI-ism pass** — apply `ai-isms.md`. Flag patterns, don't just reword silently; the user wants to learn what to avoid.
3. **SEO pass** — apply `seo-checklist.md` at the depth chosen in Step 2 only. Do not run full-audit checks if the user chose basics.

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

For long content (over ~1,500 words), save the output as a markdown file and share it rather than flooding the chat.

## Principles

- Preserve the author's meaning and structure. Fix problems; don't rewrite for the sake of it.
- The tone-of-voice file wins over generic style preferences. If it conflicts with an AI-ism rule, follow the tone file and note the conflict.
- Be specific in the change log — vague entries like "improved flow" are useless. Name the rule applied.
- If the content is clean in a category, say so briefly rather than inventing issues.
- When the brand tone-of-voice file still contains template placeholders, mention that filling it in will improve results, then proceed with sensible defaults.
