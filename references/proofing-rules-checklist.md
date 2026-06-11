# Proofing Rules Checklist (UK English)

Apply every rule below. Quote the offending snippet when flagging an issue.

Each section carries a **default severity** (error / warning / comment) used by the report level setting. Adjust by judgement where a specific instance is clearly more or less serious, and note exceptions marked within a section.

## 1. UK English spelling — mandatory _(default severity: error)_

Flag and correct all US spellings, including:

- -ize/-ization → -ise/-isation (organise, optimisation, realise)
- -or → -our (colour, behaviour, favour)
- -er → -re (centre, metre, fibre)
- -og → -ogue (catalogue, dialogue)
- -ense → -ence (licence/defence as nouns; note "license" stays as a verb)
- Single → double L in inflections (travelling, modelling, cancelled)
- program → programme (except computer programs)
- check → cheque (payments), gray → grey, tire → tyre, aluminum → aluminium
- Verb/noun pairs: practise (verb) / practice (noun); license (verb) / licence (noun); advise (verb) / advice (noun)

## 2. UK conventions _(default severity: error; the en dash rule below sets its own)_

- Dates: 10 June 2026, not June 10, 2026
- Punctuation outside quotation marks unless part of the quote
- Single quotation marks acceptable as primary (follow tone-of-voice file if specified)
- Full stops omitted in abbreviations: Mr, Dr, eg/e.g. per tone file
- "While" not "whilst" unless the tone file says otherwise (whilst reads dated)
- £ before figures, no space (£50)
- **En dashes (–):** normal British English usage — ranges (10–20), connectors (London–Paris), modifiers (post–Second World War), and spaced en dashes as parenthetical dashes — is correct and is **not** an issue. Flag as an error only when genuinely wrong (e.g. a hyphen where a range/connector needs an en dash, or mixed dash styles within the same document — the mixing is the inconsistency error). Otherwise, mention dash usage only as a general comment, and only if there's something genuinely worth noting. The user can override this and ask for all en dash use to be reported as errors.

## 3. Grammar _(default severity: error)_

- Subject–verb agreement, especially with collective nouns (UK allows plural: "the team are" — flag inconsistency, not the choice)
- Dangling and misplaced modifiers
- Pronoun ambiguity ("it", "this", "they" with unclear referents)
- Incorrect apostrophes (its/it's, plural vs possessive)
- Comma splices and run-on sentences
- Inconsistent tense within a section
- "Less" vs "fewer", "amount" vs "number", "that" vs "which" (restrictive vs non-restrictive)

## 4. Consistency _(default severity: warning)_

- One spelling per term throughout (e-commerce vs ecommerce; email vs e-mail)
- Consistent capitalisation of product names, headings (pick sentence case or title case and stick to it)
- Consistent number style: spell out one to nine, numerals for 10+ (unless tone file overrides)
- Consistent serial (Oxford) comma usage — either always or never
- Consistent list punctuation and parallel structure in bullet lists

## 5. Web-specific checks _(default severity: broken/placeholder links are errors; the rest are warnings)_

- Broken or placeholder links ([link], lorem ipsum, TBC, XXX)
- Link text that says "click here" or "read more" with no context — flag for descriptive anchor text
- Missing or duplicated headings; heading text that doesn't match the section content
- Phone numbers, emails, addresses formatted consistently
- Trademark/brand names spelt as the owner spells them (e.g. WordPress, iPhone, LinkedIn)
- Visible URL consistency: all either include or omit "www", and all either include or omit trailing slashes — flag mixed styles as an inconsistency (applies to URLs shown in the copy and link destinations where visible)

## 6. Clarity and concision _(default severity: comment)_

- Passive voice where active is clearer (flag, don't ban — sometimes passive is right)
- Redundant pairs ("each and every", "first and foremost")
- Nominalisations ("make a decision" → "decide", "conduct an analysis" → "analyse")
- Sentences over ~30 words — flag for possible splitting
- Jargon undefined for the page's audience
