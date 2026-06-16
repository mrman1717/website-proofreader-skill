# On-Page SEO Checklist (current best practices, mid-2026)

Run only the level the user chose. Each level includes everything in the levels above it. Where the page's HTML metadata isn't provided (e.g. pasted body copy only), say which checks couldn't be run and what to supply.

You need a **target keyword/topic**. If not given, infer it from the content, state the assumption, and invite correction.

**Default severities** (used by the report level setting): a **missing** required element (no title tag, no meta description, no H1, broken links) is an **error**; a present-but-weak element (too long/short, keyword absent, duplicate, vague) is a **warning**; opportunities and suggestions (structured data ideas, structure improvements, AI-search formatting) are **comments**. Adjust by judgement for clear-cut cases.

## Level 1 — Basics

**Title tag**
- Present, unique, ~50–60 characters
- Target keyword near the front, written for humans (compelling, not stuffed)

**Meta description**
- Present, ~120–155 characters
- Includes the keyword naturally; written to earn the click (benefit or answer, not a summary of headings)

**Headings**
- Exactly one H1, containing the target keyword
- Logical hierarchy: no skipped levels (H1 → H2 → H3), no orphan H4s
- Each heading accurately describes its section; the first sentence under a heading should directly answer or address what the heading promises

**Links**
- Descriptive anchor text — never "click here" / "read more" alone
- Internal links to relevant pages where natural
- At least a couple of external links to credible, relevant sources where the content makes claims
- No broken/placeholder links
- Email addresses deliberately obfuscated against spam (JavaScript cloaking, HTML-entity encoding, or "protected from spambots"-style markers — standard in Joomla and many other CMSs) are an **intentional anti-spam choice, not an error or warning**. Don't tell the user to "fix" a deliberate measure. Note it at most as a general comment, and only when there's no accessible contact fallback (a contact form or page) — present the spam-vs-findability tradeoff neutrally.

## Level 2 — Standard (basics + keyword usage & readability)

**Keyword usage**
- Target keyword appears in the first 100 words, naturally
- Related terms and synonyms used throughout (semantic coverage), not the exact phrase repeated — flag keyword stuffing as a negative
- Keyword or close variant in at least one H2
- URL slug (if provided): short, descriptive, contains the keyword

**Search intent match**
- Does the content actually answer what someone searching this term wants? Flag mismatches (e.g. a sales page targeting an informational query)
- Is the core answer near the top, or buried?

**Readability**
- Short paragraphs (2–4 sentences) for web reading
- Mixed sentence lengths; average around 15–20 words
- Plain words over jargon for the audience; define unavoidable jargon
- Scannable: subheadings roughly every 150–300 words, lists where genuinely list-like
- Front-load key information (inverted pyramid)

## Level 3 — Full audit (standard + structure, images, AI-search visibility)

**Content structure**
- Clear value within the first screen — what is this page and why should I stay?
- Self-contained sections: each heading + its first paragraph should make sense extracted on its own (this is what AI search engines lift into answers)
- Question-style H2s where they match real queries, answered directly underneath
- A logical narrative order; no repeated points across sections
- Clear call to action where appropriate; one primary CTA, not five competing ones

**Images**
- Every image has descriptive alt text containing relevant terms where natural (never stuffed)
- Descriptive filenames if visible (hero-bristol-office.jpg, not IMG_4021.jpg)
- Flag obviously oversized/undescribed images for performance (note: full performance testing is out of scope for copy review)

**AI-search visibility (AI Overviews, chatbots, answer engines)**
- Direct, quotable answers: key facts stated plainly in standalone sentences
- Definitions, steps, and comparisons formatted so they can be extracted (numbered steps for processes, tables for comparisons)
- Demonstrated experience/expertise signals in the copy: specifics, first-hand detail, named authors or credentials where relevant (E-E-A-T)
- Dates and facts current; flag stale years or outdated claims
- **Structured data (schema markup):** JSON-LD lives in `<script type="application/ld+json">` blocks, which are **not** part of a page's rendered/visible text — fetched or pasted body copy will not show it even when it is present on the page. Before recommending any schema, check the raw HTML/page source for existing `application/ld+json` and note what type(s) are already there (FAQPage, Product, Article, etc.). Only state that schema is "missing" or "not detected" if you have actually examined the raw HTML and confirmed its absence.
- If you only have rendered text (most fetched pages, pasted copy), do **not** claim structured data is absent. Phrase the suggestion conditionally — "if FAQ schema isn't already implemented, this page is a good candidate" — and tell the user how to confirm (view page source, or search the source for `application/ld+json`). Where schema is genuinely absent or could be extended, suggest opportunities (FAQ, HowTo, Product, Article) — recommend only; implementation is a dev task.

**Freshness and trust**
- Visible publish/update date recommended for time-sensitive content
- Claims sourced or sourceable; flag uncited statistics
- Consistent brand/entity naming throughout (helps entity recognition)

## Reporting

For every SEO issue: state what's wrong, why it matters (one line), and the specific fix — ideally with rewritten example text (e.g. propose the actual improved title tag, not "improve the title").

## Sources

The checks above synthesise established on-page SEO fundamentals with
current (mid-2026) guidance from:

- Semrush — On-page SEO checklist: The complete task list for 2026 —
  https://www.semrush.com/blog/on-page-seo-checklist/
- Backlinko — On-Page SEO: The Definitive Guide —
  https://backlinko.com/on-page-seo
- Loganix — 25 On-Page SEO Tips that WORK in 2026 —
  https://loganix.com/on-page-seo-tips/
- WordStream — On-Page SEO: The Complete Guide for 2026 —
  https://www.wordstream.com/blog/ws/2022/04/06/on-page-seo
- Hosting.com — 9 Proven On-Page SEO Tactics for 2026 —
  https://hosting.com/blog/on-page-seo-checklist/
- Svitla Systems — SEO Strategy Best Practices for 2026 —
  https://svitla.com/blog/seo-best-practices/

Last reviewed: June 2026. External links may go stale; verify before
relying on them.
