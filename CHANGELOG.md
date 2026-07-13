# Changelog

All notable changes to the website-proofreader skill are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/) principles; versioning follows [Semantic Versioning](https://semver.org/).
The authoritative version number and date live in the `metadata` block of SKILL.md.

## [1.6.0] — 2026-07-09

### Added
- Version announcement on start: the skill now states which version is running (read from SKILL.md's frontmatter `metadata`) as the first line of every run, so it's clear which copy is active — useful because installed and packaged copies can silently lag the repo. The number is not hard-coded in the workflow text; the frontmatter remains its single source.

## [1.5.0] — 2026-07-08

### Fixed
- Reporting accuracy / fabricated examples: when flagging an issue the skill was inventing plausible-sounding examples instead of quoting the real text — e.g. attributing inconsistent internal-link domains to "Get started" / "More about us" CTAs that weren't the actual offenders. It now must quote the offending text **verbatim** (real anchor text and real destination URL), cite the specific page, and for a recurring/site-wide issue give the true count and list the actual instances rather than a vague "many". A new principle in SKILL.md bans fabricating evidence outright.
- Link-destination blind spot: a link's target lives in its `href`, which is stripped from rendered/fetched text (only the anchor text survives). The skill was guessing where links pointed. It now treats link-destination checks — where a link goes, and www/protocol/trailing-slash consistency — as raw-markup-only, and says the check needs the page source instead of asserting a destination it can't see.

### Added
- SEO checklist (Level 1 — Links): internal-link canonical-host check — internal links should point to the site's canonical host and protocol (the www-or-non-www, https version the site redirects to) to avoid a needless redirect hop and split link equity. Previously the www/non-www consistency check lived only in the proofing checklist, so an SEO-only run had nothing grounding it.

### Changed
- SKILL.md: Step 2 adds link `href` values to the raw-markup items and notes rendered text hides them; Step 4 requires verbatim quoting, real per-page locations, and enumerated instances (no "many"); seo-checklist.md Reporting adds the same verbatim/location/enumeration requirement.
- proofing-rules-checklist.md: the visible-URL-consistency check now requires quoting the real anchor text + destination URL + page and a true count, and notes destinations are only visible in the raw markup.

## [1.4.0] — 2026-06-19

### Added
- Configurable English variant. The proofreader is no longer hard-wired to UK English: it resolves which variant to use as explicit request in chat → the **Language variant** set in `tone-of-voice.md` → **UK English** (unchanged default). UK, US, Australian, and Canadian English are the expected variants, and any variant named in the request is honoured. It states the active variant in one line rather than adding a setup question, and switches on request.

### Changed
- `references/proofing-rules-checklist.md`: Section 1 (spelling) and Section 2 (conventions) are now variant-aware — UK English remains the worked example/default, with the US/AU/CA equivalents noted (dates, quotation marks, currency, "-ize" spellings, etc.). The pass no longer flags spellings or conventions that are correct in the active variant.
- `references/tone-of-voice.md`: added a **Language variant** style setting (default UK English); the default-voice line no longer hard-codes "British English".
- SKILL.md: pass 1, the severity-tier example, the intro, and the trigger description now reference the active variant instead of hard-coded UK English; Step 3 documents how the variant is resolved and announced (stated, not asked).
- README.md: documents the UK-English default and how to change it.

## [1.3.3] — 2026-06-19

### Fixed
- Over-triggering: the skill was activating too often and on unrelated prompts. The trigger `description` is rewritten to (1) anchor every trigger to the *written content of a website/web page* rather than generic verbs like "check", "review", or "edit"; (2) require proofreading/editing/SEO *intent* instead of firing on a bare pasted URL; and (3) add an explicit **Do NOT trigger** list — code review/editing, general non-website writing (emails, essays, reports), summarising or answering questions about a page, fetching a URL for research, and technical/off-page SEO.

## [1.3.2] — 2026-06-16

### Fixed
- Stale-cache re-runs: the page cache is now scoped to the current job (across its 10-page batches) only. A fresh run re-fetches the live page instead of reusing an earlier run's cache, and the skill always re-fetches when the user says they've updated the page — so already-fixed issues (e.g. an updated copyright year, a removed COVID-19 notice) are no longer reported from a stale copy.
- Deliberately obfuscated email addresses (JavaScript cloaking, HTML-entity encoding, "protected from spambots" markers — standard in Joomla and other CMSs) are no longer flagged as a warning. They're treated as an intentional anti-spam choice: noted at most as a general comment, and only when there's no accessible contact fallback.

## [1.3.1] — 2026-06-16

### Fixed
- Structured-data false negatives: the SEO pass no longer reports schema (FAQ, Product, etc.) as "missing"/"not detected" when working from rendered text. JSON-LD lives in `<script type="application/ld+json">` blocks that are stripped from a page's visible text, so absence can't be assumed from rendered copy alone. The skill now checks the raw HTML/page source for existing `application/ld+json` before recommending schema, and where only rendered text is available, phrases the suggestion conditionally and tells the user how to verify.
- SKILL.md Step 2: structured data added to the list of raw-markup items to check on fetched/uploaded HTML, with a note that fetched pages are often reduced to rendered text (which strips `<script>` JSON-LD).

## [1.3.0] — 2026-06-11

### Changed
- Workflow restructured: content is identified first (now Step 2), then all applicable setup questions are asked in one batch (now Step 3) — including the multi-page result format and target keyword, which previously floated in other steps.
- Output templates now show an explicit **[severity]** marker on every change log/report entry.
- Reference checklists tag each section with a default severity (error / warning / comment), making report-level filtering consistent between runs: spelling/grammar/UK conventions are errors, consistency and AI-isms are warnings (banned tone-of-voice words are errors), clarity is comment-level, and SEO severities follow missing = error / weak = warning / opportunity = comment.
- Page cache for multi-page jobs must live in a temp location outside the user's project folders, so it can't be committed or packaged.
- seo-checklist.md Sources pruned to higher-authority references.

### Added
- README: Claude Code / desktop installation instructions (copy the folder to `~/.claude/skills/`).

## [1.2.2] — 2026-06-11

### Added
- Crawl hygiene rules: content pages only — skip archives/tag listings, pagination, search results, query-string/fragment duplicates, feeds, and non-HTML files; respect noindex and canonical signals where visible. User-listed URLs override the filters.
- No-web-access handling: if the environment can't fetch URLs, the skill says so up front and asks for pasted or uploaded content instead of attempting a crawl.

## [1.2.1] — 2026-06-11

### Fixed
- Step 2 intro no longer says to ask every setup question every time, which contradicted the skip rules and Question 4's silent defaults.
- ai-isms.md: removed duplicated "elevate" from the vocabulary list.

### Added
- Output format guidance for URL-sourced content: recommend the annotated report (a rewrite isn't re-injectable into a live site), while still offering polished copy.
- Fetch-failure handling: unfetchable or empty pages are listed as "could not check" with the reason and a paste/upload fallback; never silently skipped.

## [1.2.0] — 2026-06-10

### Added
- Report level setting: errors only / errors + warnings / full (errors, warnings, and general comments). Defaults to full; suppressed issues are counted in a one-line note. Severity tiers (error / warning / general comment) defined in SKILL.md.
- Explanation detail setting: verbose (default) or token saver (one short line per issue).
- Proofing checklist: visible URL consistency check — all URLs should consistently include or omit "www" and trailing slashes.

### Changed
- En dashes: normal British English usage (ranges, connectors, modifiers, parenthetical dashes) is no longer flagged; only genuine errors (wrong dash for the job, mixed dash styles) are errors, with anything else at most a general comment. The user can opt in to having all en dash use reported as errors.
- ai-isms.md: em dash overuse rule clarified to exclude en dashes.

## [1.1.2] — 2026-06-10

### Added
- Sources section in seo-checklist.md.

## [1.1.1] — 2026-06-10

### Added
- MIT licence: `license: MIT` in SKILL.md frontmatter plus a LICENSE file.
- SKILL.md metadata: `author` (mrman1717) and `repository` (public GitHub repo URL).

### Changed
- README.md: added licence section; LICENSE added to the file structure listing.

## [1.1.0] — 2026-06-10

### Added
- Mode selection at the start of each run: proofreader only, SEO checker only, or both. Setup questions that don't apply to the chosen mode are skipped.
- URL-based content sources: single page URL, whole-site crawl from a main URL (sitemap.xml/robots.txt first, internal links as fallback), sitemap files, and URL lists (single site only — multi-site lists are rejected).
- Multi-page handling: 10-page batch cap with continuation prompt, local page caching when running in an environment with file access, and a per-run choice between one combined report or per-page outputs plus a site-wide summary.

### Changed
- SKILL.md: Step 4 passes and Step 5 output templates now respect the chosen mode; multi-page jobs always saved as files.
- README.md: updated usage instructions for the new modes and content sources.

## [1.0.1] — 2026-06-10

### Added
- CHANGELOG.md — version history now travels with the skill.

### Changed
- README.md: removed the standalone version section (SKILL.md metadata is now the single authoritative location for version and date); added CHANGELOG.md to the file structure listing.

## [1.0.0] — 2026-06-10

### Added
- Initial release.
- SKILL.md: three-pass workflow (proofing, AI-isms, SEO) with per-run choice of output format (polished copy + change log, or annotated report) and SEO depth (basics / standard / full audit). UK English enforced.
- references/proofing-rules-checklist.md: UK spelling and conventions, grammar, consistency, web-specific, and clarity checks.
- references/ai-isms.md: overused AI vocabulary, filler, formulaic structures, vagueness patterns, and rhythm checks.
- references/seo-checklist.md: on-page SEO checks at three depth levels, including AI-search visibility (mid-2026 best practices).
- references/tone-of-voice.md: brand voice template with sensible defaults and placeholders.
- README.md: installation, usage, and customisation guide.
