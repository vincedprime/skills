---
name: deslop
description: Use when writing or editing any prose for a human reader (answers, docs, bug notes, PR descriptions, messages) so it is quick to read. Covers order, cutting, confidence, and density.
---

# Deslop

Goal: the reader gets the point on one pass, without rebuilding the story or decoding shorthand.

This skill covers document-level problems: order, selection, confidence, density. It does not cover sentence-level AI tells (inflated words, forced triads, "not X but Y"). If the `humanizer` skill is installed, run it after this one for those.

## When to apply

- Before sending any prose you wrote: answers, summaries, docs, bug notes, PR descriptions, commit bodies, messages.
- When asked to edit, shorten, clean up, deslop, or "humanize" existing text.

Do not change code, data, quoted text, link targets, or frontmatter. Do not add or alter facts. If a needed detail is missing, ask or mark it as missing.

## Rules

### 1. Answer first

The first sentence gives the conclusion or the thing asked for. Background follows only if the reader needs it.

- Before: "I looked at the export flow and compared the three clients. After tracing the payloads, it appears that..."
- After: "Expense exports show duplicate columns because the library appends columns the expense row already has."

### 2. Order by what the reader needs

Do not order by what you did or by topic investigated. Default order for a finding: what is wrong or what was asked, why, who or what else is affected, what is open, what to do next. Describe the process only when the process is the point.

### 3. Cut what does not change what the reader does or believes

Being true and related is not enough. For each fact ask: would the reader act or decide differently without it? If not, delete it or move it to a one-line note at the end.

### 4. Spend detail unevenly

Give the hard or surprising part a full explanation. Give obvious parts one line. Equal detail everywhere hides what matters.

### 5. One concrete example for anything non-trivial

Show a real input and what happens to it, step by step, in full sentences.

- Before: "The library extends the include-list for custom row types, causing mismatches."
- After: "The UI asks for 5 columns. The library adds Location and Grade. The expense row has no Location field, so that cell is blank."

### 6. Mark confidence

Say which claims were verified, which are inferred, and which are unchecked. Do not state all three in the same tone.

- Verified: say how, briefly ("confirmed in the export code").
- Inferred: "should", "probably", with the reason.
- Unchecked: say so ("not verified on the UI yet").

Keep a qualifier when it carries this information. Remove qualifiers that only soften ("it may potentially", "arguably").

### 7. End with the next step or open decision

If something is undecided, list the options and what blocks the choice. If nothing is open, stop. No closing summary that repeats the body.

### 8. Limit identifiers

Use a class, method, file, or ticket name only when the reader will search for it or already uses it. Otherwise describe the behavior ("the export library"). After the first mention, use a short plain name instead of repeating the full identifier.

### 9. Full sentences, no shorthand

No arrows, dropped articles, or invented abbreviations in prose. Terse fragments move the work to the reader. Lists of parallel items may be fragments.

### 10. One name per thing

Pick a term and keep it. Do not rotate synonyms; the reader will assume a new word means a new thing.

### 11. Define jargon on first use

If a term or acronym is unavoidable and the reader may not know it, define it in a few words where it first appears.

### 12. Formatting carries structure only

- Table: only when the reader compares items across the same attributes.
- Numbered list: only for a sequence.
- Bold: only for terms the reader scans for. Not for emphasis.
- Reasoning goes in sentences, not bullets.

### 13. Length matches the question

A one-line question gets a short answer. A bug note fits on one screen. Offer extra material in one line instead of including it.

## Process

1. State the main point in one sentence. If you cannot, the content is not ready; find the point first.
2. List what the reader must know to act on it. Everything else is a candidate to cut.
3. Write or rewrite in the order from rule 2. Do not treat the original structure as fixed.
4. Check against the source: no fact, number, name, or claim lost or changed. No confidence marker removed.
5. Re-read as the reader. Fix any sentence that needs a second read.

## Output

- Writing your own text: output the final text only.
- Editing pasted text: output the rewrite, then up to three lines on what was cut or moved, so the user can restore anything they need.
- Editing a file: change prose only, then list the sections changed.

## When not to act

- Quotations, legal text, and text the user says must stay verbatim.
- Reference material meant for lookup (API tables, changelogs). Rules 8 to 12 still apply; rules 1 to 7 do not.
- A user style sample or explicit instruction overrides these rules.
