---
name: review-notes
description: Audit slipbox and literature notes against the knowledge_base conventions (R1–R6) — layer placement, atomicity, title quality, source-tether/context-independence, extraction candidates, link quality. Use when asked to review, audit, lint, or check notes. The argument selects the layer.
disable-model-invocation: true
user-invocable: true
argument-hint: "[slipbox | literature | all]  (default: all)"
allowed-tools: Read, Grep, Glob
---

# review-notes

Read-only, report-only audit against the conventions in `CLAUDE.md` / the repo README. Never edit, move, or delete files — report findings and let the author act. Read the conventions doc first; it is the source of truth for what the rules mean.

Fleeting notes are **out of scope** here (they have no R-checks). Use `/triage-fleeting`.

## Dispatch on `$ARGUMENTS`

- `slipbox` → run **R1, R2, R3, R4, R6** over `slipbox/`.
- `literature` → run **R3, R5** over `literature_notes/`.
- `all` or empty → run everything over both folders.

## What the reviewer can and cannot do

State this in the report. The reviewer **cannot follow wikilinks to read their targets**, so R2, R4, and R6 are limited to surface-detectable signals. Mark borderline cases `REVIEW` (needs the author's judgment), never `FAIL`. Do not invent violations to look thorough.

## Checks

### R1 — Title is a claim (slipbox)
- **PASS:** the descriptive title states a defensible claim (a sentence you could disagree with).
- **FAIL:** the title is a bare topic/noun phrase ("discounting") rather than a claim ("discounting is what makes infinite-horizon value functions converge").
- Judge the descriptive title, not the Luhmann ID.

### R2 — Single claim, judged by linkability (slipbox)
- **PASS:** one claim. Also passes if several points are bundled but **none** is independently linkable — long single-claim cards are fine.
- **FAIL:** 2+ claims bundled **and** at least one sub-claim is something a peer card would plausibly link to on its own.
- Never flag on length alone. Splitting is justified only when it buys linkability.
- Linkability unclear without reading neighbors → `REVIEW`.

### R3 — Layer placement
- Direction depends on the layer being reviewed:
  - In `slipbox/`: **FAIL** if the card is source-tethered (relies on "the paper argues…", "Ch. 3 says…") → belongs in `literature_notes/`; or if it is verbatim source text → belongs in `references/`.
  - In `literature_notes/`: **FAIL** if the note is a standalone source-free claim → promote to `slipbox/` (overlaps R5); or if it is the source's own verbatim words rather than the author's digest → belongs in `references/`.
- **PASS:** layer matches the note's organizing principle (source-sized upstream, claim-sized in slipbox).

### R4 — Context-independence from the external source (slipbox)
- The tether test in reverse.
- **FAIL:** the card collapses if you delete its source attribution — framing leans on where the idea came from.
- **PASS:** the card stands as a claim; the source is only a citation.
- **Not a violation:** depending on *other slipbox cards* via wikilinks. R4 is external-source dependency only.
- Independence hinges on a linked card's content → `REVIEW`.

### R5 — Extraction candidates (literature)
- Not pass/fail. Surface bullets that read as **defensible standalone claims** and have not yet been promoted.
- Output: list each candidate with its file, as a prompt for the author.
- Many-bullet literature notes are **correct** (one source = one note), not a defect.

### R6 — Link quality (slipbox)
- **FAIL** only when **both** hold at once:
  1. the link sits in an unanchored list — no surrounding prose, no section header giving context; **and**
  2. the link title gives no thematic hint connecting it to this card's claim.
- Either condition alone is acceptable — do not flag.
- Secondary surface smell (report as `REVIEW`): a bare sequential chain (`t2 → t2a → t2b`) mirroring source order with no annotation, where the relation looks topical, not conceptual. Verdict belongs to the author.

## Output format

Group findings by check, most actionable first:

```
[FAIL|REVIEW] R{n} — <file path>
  issue:  <one line>
  fix:    <one line suggested action>
```

End with a summary table (one row per check run, columns: passed / FAIL / REVIEW) and a short coverage note on what couldn't be verified because link targets weren't read.

Verification only — propose fixes, never apply them.
