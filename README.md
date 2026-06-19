# Website Proofreader — Claude Skill

Proofreads website content in three passes:

1. **Spelling & grammar** — your chosen English variant enforced (UK English by default), plus consistency and web-specific checks
2. **AI-isms** — detects and removes overused AI words, phrases, and formulaic structures
3. **On-page SEO** — checks against current (2026) best practices, including AI-search visibility

## What it asks you each run

- **Mode:** proofreader only / SEO checker only / both
- **Output format:** polished copy + change log, or an annotated report (no rewrite)
- **SEO depth:** basics / standard / full audit
- **Report level:** errors only / errors + warnings / full (+ general comments) — defaults to full
- **Explanation detail:** verbose (default) or token saver (one line per issue)
- A target keyword, if one isn't obvious

All applicable questions are asked together in one batch after the content is identified; questions that don't apply to your chosen mode or content source are skipped. Issues are graded error / warning / comment, so you can filter the report to just what matters.

**Language variant.** It proofreads in **UK English by default** — this isn't a per-run question. To change it, set a different **Language variant** (UK / US / Australian / Canadian) in your `tone-of-voice.md`, or just say so in chat (e.g. *"proofread this in US English"*). It states which variant it's using at the start of each run.

## How to use it

1. Install the skill:
   - **Claude.ai:** Settings → Capabilities → Skills → Upload the `.skill` file.
   - **Claude Code / Claude desktop:** copy the `website-proofreader/` folder into `~/.claude/skills/` (creating the folder if needed), then start a new session.
2. Start a chat and give it your content in any of these ways:
   - Paste the copy, or upload it (.txt, .md, .docx, .pdf, .html)
   - A single page URL
   - A main site URL to crawl (sitemap first, then internal links; max 10 pages per batch)
   - A sitemap (XML or similar)
   - A list of URLs (one site at a time)
3. Say something like *"Proofread this landing page"* — the skill triggers automatically.
4. Answer the setup questions, then review the output. Multi-page jobs can be delivered as one combined report or per-page outputs plus a site-wide summary.

## Customising it for your brand

Edit `references/tone-of-voice.md` — it's a template with placeholders for your brand voice, preferred/banned vocabulary, and style choices, plus a slot for sample copy so Claude can match your rhythm. Re-zip and re-upload after editing.

You can also tighten or extend:

- `references/proofing-rules-checklist.md` — house style rules
- `references/ai-isms.md` — words/patterns to ban
- `references/seo-checklist.md` — SEO checks per depth level

## File structure

```
website-proofreader/
├── SKILL.md                          # workflow Claude follows
├── README.md                         # this file
├── CHANGELOG.md                      # version history
├── LICENSE                           # MIT
└── references/
    ├── tone-of-voice.md
    ├── proofing-rules-checklist.md
    ├── ai-isms.md
    └── seo-checklist.md
```

## Version

The current version number and date live in the `metadata` block of `SKILL.md`. See `CHANGELOG.md` for version history.

## Licence

Released under the [MIT License](LICENSE). Source: [github.com/mrman1717/website-proofreader-skill](https://github.com/mrman1717/website-proofreader-skill).
