# Changelog

All notable changes to the website-proofreader skill are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/) principles; versioning follows [Semantic Versioning](https://semver.org/).
The authoritative version number and date live in the `metadata` block of SKILL.md.

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
