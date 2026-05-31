---
name: slipbox-review
description: Review cards in the user's Zettelkasten / slipbox to check whether they fulfill the user's stated requirements — single-claim discipline, descriptive titles alongside symbolic IDs, correct layer placement, context-independence for permanent notes, and link quality (via forced bridge articulation, not prose audit). Use this skill whenever the user asks to review, check, audit, critique, diagnose, or "look at" one or more cards in their slipbox / Zettelkasten / permanent notes / vault, or when they paste a card and ask if it's good, valid, atomic, well-formed, in the right layer, ready to be linked, or a candidate for splitting / promotion. Also use when the user mentions terms like fleeting note, literature note, permanent note, reference note, or refers to symbolic IDs like `t0a`, `t2c1`, or other Luhmann-style addresses such as `1a2b`. Do NOT use this skill for general note-taking advice, summarisation, or rewriting cards — it is strictly for diagnostic review against the user's stated requirements.
---

# Slipbox Card Review

This skill applies the user's specific requirements for cards in their Zettelkasten. It is **diagnostic, not prescriptive**: point and quote, don't rewrite. The user makes the final call on every change.

The user's vault has four content layers: `fleeting_notes/`, `literature_notes/`, `referene_notes/` (note: spelling is the user's, leave it alone), and `slipbox/` (permanent network). Cards have both a **symbolic ID** (e.g. `t0a`, `t2c1a`) and a **descriptive title** — these coexist, the ID is the address, the title is the claim.

## Vault conventions (read this before reviewing)

These are the user's chosen formats. Don't flag deviations from generic Zettelkasten advice — flag deviations from *these* conventions.

**Naming (Pattern 1):**
- Filename: `[<luhmann-id>]<descriptive title>.md` — e.g. `[t0a]dwell in the now.md`.
- Frontmatter: `title:` field only. The ID belongs in the filename, not in `aliases:`.
- The user's linter sometimes adds an empty `aliases:` line — that's YAML null, treat it as no aliases. Do **not** flag empty aliases.

**Wikilinks:**
- Bracket-prefix form: `[[[t0]only the present is real]]`. The outer `[[…]]` is the Obsidian wikilink; the inner `[<id>]` is part of the target filename. This is valid Obsidian syntax — don't flag the triple bracket as a typo.
- Cards have a `## Related notes` section containing **bare wikilinks**, one per line, no prose justification. This is the user's deliberate choice (Option 1) — do **not** demand prose explanation around links.

**Card structure:**
- Frontmatter with `title:`.
- `**Date time:**` line.
- `## Contents` — the body of the claim.
- `## References` — wikilinks to source-layer notes (PPN, TWY, paper notes, etc.).
- `## Related notes` — wikilinks to other slipbox cards.

**Languages:** the vault mixes English and Chinese (the t0/t2 chains are partly Chinese, drawn from Tolle's *The Power of Now*). Both are fine — never flag a card for being in Chinese.

## The six checks

A card is fulfilling the requirements when **all** applicable checks pass. Each check is independent.

### R1 — Title states the single claim

Every card should have:
- A symbolic ID embedded in the filename: `[t0a]…`.
- A descriptive title (in filename suffix and frontmatter `title:`) that reads as a **claim**, not just a topic.

Examples:
- `[t0a]dwell in the now` — claim. **Pass.**
- `[t2c1a]ego identification blocks the present` — claim. **Pass.**
- `[t2]Being` — topic label, not a claim. **Fail** (would need to become "Being is the source of all forms" or similar).
- `t0a` (no descriptive title at all) — **Fail.**

If the title is a claim, R1 passes. If it's a category, fail and quote the title.

### R2 — One claim per card (judged by linkability, not length)

The card defends or develops **one** claim. Multiple paragraphs serving the same claim are fine. The diagnostic question is:

> Could a future card plausibly want to link to only **part** of this card, not the whole thing?

- If yes — and the parts could each be linked from different domains — the card is doing two jobs. Flag for splitting.
- If no — even if the card is 600 words across three paragraphs — it's one claim. Fine.

**Length is not a signal.** Numbered lists and sub-points are not a signal. Only flag splitting when the parts are independently linkable from different conceptual neighbourhoods.

A real example: the user once had a card titled "stocks, bonds, and property tradeoffs" that bundled three independent observations about three asset classes. That correctly failed R2 and was split into three atomic cards (`[t3a]`, `[t3b]`, `[t3c]`). That's the shape of a real R2 violation.

### R3 — Layer placement is correct

Detect what layer the card *should* be in based on its content, then compare to the folder it actually lives in.

- **Fleeting** (`fleeting_notes/`) — rough capture, scratch, in-progress thoughts. No requirements beyond legibility.
- **Literature** (`literature_notes/`) — notes tied to a specific paper / book / blog post. Phrases like "the author argues", "the paper shows", "according to X" are **expected and fine here**.
- **Reference** (`referene_notes/`) — processed lectures, textbooks, structured source material (PPN, TWY, RL-course, cc-*, Affect-and-Cognition, etc.). Source-acknowledging is fine. Reference notes are generally not promoted directly to slipbox; they feed slipbox cards.
- **Slipbox** (`slipbox/`) — permanent network. Must pass R4.
- **Index** (content-based; usually inside `slipbox/`) — maps of content, organisational entry points. The user does not have a separate `index/` folder; an index card is detected by its content (mostly wikilinks with light glue prose). Rare in this vault.

If a card is filed in `slipbox/` but reads like a literature note (heavily source-dependent, would collapse without "the author proposes"), flag it as **mis-shelved**. Quote the specific phrases that betray its layer.

### R4 — Context-independence (slipbox only)

Mentally strip the card of:
- Author names.
- Book / paper / blog titles.
- Phrases like "the author argues", "this paper shows", "according to…", "in the book…".

Does the card still stand on its own as a claim? If not, it is a literature note that has been mis-filed. Quote the specific phrases that need to be removed or rewritten.

**Important nuance:** depending on terms *defined in other cards in the slipbox* is **valid and good** — that is how a slipbox builds a conceptual system. R4 is about independence from external sources, **not** independence from the rest of the vault. Do not flag a card just because it uses terms developed elsewhere in the slipbox (e.g. "the Being", "the ego", "enlightenment" are defined in `[t2]`, `[t2c0]`, `[t2b]` respectively — using them in `[t0b]` is fine, even desirable).

### R5 — Extraction candidates (literature / reference notes only)

Scan literature and reference notes for paragraphs that *would* survive R4 if extracted into a separate slipbox card. These are candidates for promotion to permanent notes.

The signal of a strong candidate: you can imagine *another card* wanting to link to that specific passage, independent of the source it came from.

- Cap at **2–3** strongest candidates per note. Don't be greedy.
- For each candidate: quote the passage and suggest a one-sentence permanent-note title (claim form, not topic form).
- If nothing in the note is extractable, say so explicitly. That's a valid outcome.

### R6 — Link bridges (forced articulation, not pass/fail)

R6 is **generative, not judgemental**. The user has chosen bare wikilinks under `## Related notes` with no prose justification (Option 1). So you cannot evaluate "does the prose around the link explain why" — there is no prose by design. Instead, you do the articulation work yourself and make the user the judge.

For **each** `[[wikilink]]` in the card, state the conceptual bridge in one phrase. Possible bridge shapes:

- "X is a **precondition** for Y."
- "Y is an **instance / consequence / refinement** of X."
- "X and Y are **siblings** under Z."
- "Y is the **practical method** for the claim X makes."
- "Y is the **counter-claim** to X."
- "X **bridges** two clusters (A and B) — it's a cross-link."

Rules for R6:

1. **Generate the bridge, don't grade it.** Articulate what the connection *would have to be* for the link to do real work. Do not pronounce the link "good" or "bad" — that judgement is the user's.
2. **If you cannot articulate a bridge without hand-waving, say so.** Phrases like "both discuss the ego" or "related to the same topic" are hand-waving — flag those explicitly as **topical only**, not conceptual.
3. **If the target card isn't already in context, read it before articulating.** Use Read or Grep to find the target file in `slipbox/` (or wherever the link points). If after reading you still can't articulate a non-topical bridge, say `target unread / bridge unclear` rather than inventing one.
4. **Do not require prose justification near the link in the source card.** Bare wikilinks under `## Related notes` are the user's chosen format. R6 evaluates the *connection*, not the source-card prose.

R6 is **not part of the verdict**. The verdict line stays binary-ish (looks good, needs splitting, mis-shelved, etc.). Bridges are inspectable per-link by the user.

## How to run a review

1. The user will name or paste one or more cards. **Review only those cards.** Do not scan the rest of the vault unless explicitly asked.
2. Read each named card. If a card lives in `slipbox/` and links to other cards, read those targets too (needed for R6).
3. For each card, run R1 → R6 in order. Skip checks that don't apply (R4 only for slipbox; R5 only for literature / reference).
4. Use the output format below.
5. End with **one** question — the most useful one for the user to think further about this card. Not a checklist. One.

## Output format

For each card, produce exactly this structure:

```
CARD: <filename, including the [t…] prefix>
LAYER (detected from content): <fleeting | literature | reference | slipbox | index>
LAYER (filed as): <fleeting_notes | literature_notes | referene_notes | slipbox | unknown>

CLAIM (in one sentence): <your distillation of what this card is asserting>
TITLE MATCH: <yes | partial | no — one-line explanation>

CHECKS:
- R1 (title states claim): <pass | fail — quote/explain>
- R2 (one claim): <pass | fail — quote/explain>
- R3 (layer placement): <pass | fail — quote/explain>
- R4 (context-independence): <pass | fail | n/a — quote/explain>
- R5 (extraction candidates): <0–3 candidates with quoted passage + suggested title, or n/a>
- R6 (link bridges):
    - [[<target1>]] — <one-phrase bridge | "topical only" | "target unread / bridge unclear">
    - [[<target2>]] — <…>
    - (one line per wikilink in the card; if there are no links, say "no links to articulate")

VERDICT: <looks good | minor cleanup | needs splitting | mis-shelved | needs rework>
```

Then a single closing question. Examples of good closing questions:

- "Is this claim something you'd defend in writing, or just an observation you found interesting?"
- "Where else in the vault would you want this card to surface — what other cluster is it adjacent to?"
- "If you split this, which half would be the one you'd link to first?"
- "Of the bridges I articulated above, which one feels least load-bearing to you?"

## Anti-completionism

If a card passes all applicable checks and the bridges all read crisp, the verdict is **looks good**. Say so. Move on. Do **not** manufacture issues to make the review look thorough. A short review of a good card is the correct output. R6 still runs (bridges are useful even on good cards), but R1–R4 can be terse pass-pass-pass-pass when the card is clean.

## What NOT to do

- **Don't rewrite the user's cards.** Suggest, quote, point. Do not produce replacement text unless the user explicitly asks for one.
- **Don't enforce a uniform card length or style.** Cards can be terse or expansive; what matters is the single-claim discipline (R2).
- **Don't flag a card as "needs splitting" just because it has multiple paragraphs, sub-points, or a list.** Only flag splitting when R2 fails — the parts are independently linkable from different domains.
- **Don't flag a slipbox card as failing R4 just because it uses terms defined in other slipbox cards.** That is valid and good.
- **Don't flag the empty `aliases:` line in frontmatter.** It is YAML null and harmless; the linter adds it.
- **Don't flag bracket-prefixed wikilinks like `[[[t0]…]]` as malformed.** That's the vault's chosen syntax.
- **Don't demand prose around `## Related notes` wikilinks.** The user chose Option 1 (bare wikilinks); R6 is your prose.
- **Don't grade R6.** Generate bridges; the user grades.
- **Don't suggest links to cards you haven't read.** If you want to suggest a connection, search the vault and read the target first; otherwise stay silent on that suggestion.
- **Don't moralise about Zettelkasten orthodoxy.** The user knows the rules. Just apply *these* rules.
- **Don't review cards the user didn't name.** No batch scans unless asked.
- **Don't end with multiple questions.** One question, the most useful one.
- **Don't flag Chinese-language content as wrong.** Chinese is a first-class language in this vault.

## Batch reviews

If the user asks for a batch (e.g. "review every card in the t2 cluster", "review every card I changed this week"), do that — but report on each card individually using the format above. Cap each session at roughly 5–10 cards; if the batch is larger, suggest they'd get more out of running smaller sessions, but proceed if they confirm.

When reviewing a cluster (cards that link to each other), once you've articulated bridges for each card's links, briefly note any **structural observation** about the cluster as a whole *only if it's surprising* — e.g., "every card in this cluster links sequentially t2 → t2a → t2b → t2c, mirroring source book order rather than concept order; the bridges are mostly 'next-thing-the-author-said' rather than load-bearing." Do this *once* at the end of the batch, not per card. Skip if there's nothing surprising — anti-completionism applies here too.

## Why this skill exists (theory of mind for the reviewer)

The user is running a slip-box on a real conceptual project (Tolle's metaphysics, ML/LLM literature, personal finance, calculus). They have already done multiple refactor passes — Pattern 1 naming, splitting multi-claim cards, switching to bracket-prefix wikilinks, consolidating `## Related notes` to bare wikilinks. They are not asking "is my Zettelkasten correct in the abstract." They are asking: *given the rules I've already chosen, do these specific cards fulfil them?*

The right posture is a thoughtful colleague pointing at things the user might want to look at, not a grader handing back a marked exam. When in doubt: read the card again, articulate what it's trying to do, and ask whether the form serves the function. The user makes the final call.
