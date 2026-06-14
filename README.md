# knowledge_base
My knowledge base with slipbox organization. Follows Ahrens (*How to Take Smart Notes*): **fleeting → literature → permanent (slipbox)**. A machine-populated `references/` layer runs alongside this pipeline as the verbatim source archive.

## Structure
```
fleeting_notes/    Raw, unprocessed captures
references/        Verbatim source captures (machine-populated, standing)
literature_notes/  Digested notes tethered to a source
slipbox/           Permanent notes (Zettelkasten) — the network I think with
Templates/         Reusable note skeletons used when creating new notes
```

## Note types

### Fleeting note
A raw, in-the-moment capture — a thought, observation, or question jotted down before it disappears. Fleeting notes are temporary: they exist to be processed (promoted, merged, or discarded) within days, not kept forever. No structure or sourcing requirements.

### Reference note
A verbatim capture of the source itself — full page, article, transcript, PDF — preserving the source's original structure and words. Machine-populated by the web archiver extension; I don't author these. `references/` is a **standing layer, never emptied**: permanence against link rot is its entire point.

**Capture format:** markdown is the primary capture for every source — it's greppable, diffable, and the text that anchors resolve against. Full-page MHTML is captured selectively, only when the page's visual or structural fidelity (figures, tables, layout-dependent meaning) carries information the markdown extraction drops. Heavy binaries go to R2/LFS, not plain git.

**Anchoring:** spans inside a reference note are addressed with TextQuoteSelectors (W3C Web Annotation Data Model) — `{exact, prefix, suffix}` — which match on text content rather than position, so anchors survive reformatting and pipeline changes. Anchors are always defined against the markdown capture; the MHTML is for human verification, not machine anchoring.

Reference notes and literature notes are orthogonal, not stages: the reference note preserves the *source's* structure verbatim, the literature note is *my* digest in my own words. A source can have both. The tether test doesn't apply here — a reference note *is* the source, so there's nothing to cut.

Not a reference note: verbatim transcription done as scaffolding to parse a dense source. That's a literature note mid-flight — part of writing the digest, discarded once the digest exists — and it doesn't live in `references/`.

### Literature note
A digested note about what a specific source (book, paper, lecture, article, course chapter) said, written in my own words and tethered to that source. **Tethered** means the note's framing leans on knowing where the idea came from — references like "the paper argues…" or "Ch. 3 introduces…" carry the weight. The operational test: *if I deleted the source attribution, would the note still stand?* If no, it's a literature note.

**Provenance:** when a reference capture exists, the literature note's source link points at the reference note in `references/` (ideally with a TextQuoteSelector anchor to the exact grounding span), so the digest is verifiable against the verbatim original. When no capture exists (a book, a DOI'd paper — stable, retrievable sources), the literature note cites the external source directly. Capture availability decides which.

Like reference notes, literature notes are a **standing record, never discarded**. Old unmined ones are dormant, not abandoned.

Filenames in `literature_notes/` are free-form (dates, paper slugs, topical names) — no enforced convention.

### Slipbox (permanent notes)
The Zettelkasten proper: each card defends a single claim, written so it stands on its own. The promotion from literature to slipbox is the work of **cutting the tether** — re-stating the idea in my own conceptual frame so the source becomes a citation, not the scaffolding.

"My own conceptual frame" = connecting the idea to terms and other cards already in the slipbox, not just paraphrasing. *Example:* a literature note saying "Sutton & Barto define the return as the discounted sum of future rewards" promotes to a slipbox card like "Discounting is what makes infinite-horizon value functions converge" — same content, but now a claim I'm defending, linkable to cards on convergence and value functions.

**Promotion mechanism:** the literature note stays where it is (as a source-cited record); a new slipbox card is created alongside it. They are not the same file in two places.

#### Naming and linking
Slipbox uses **Pattern 1 naming**: `[<luhmann-id>]<descriptive title>.md` (e.g., `[t0a]dwell in the now.md`). Wikilinks include the bracket prefix: `[[[t0a]dwell in the now]]` — this is required because the filename itself starts with `[`, so the link target must too.

**Luhmann IDs** encode position in the branching network by alternating letters and digits at each new depth:
- `t0`, `t2`, `t3` — top-level branches (the leading `t` is the branch family)
- `t0a`, `t0b` — direct children of `t0` (siblings of each other)
- `t2c1`, `t2c1a` — deeper descendants (`t2 → t2c → t2c1 → t2c1a`)

A new card gets an ID that places it next to its closest conceptual neighbor — sibling if it's a peer claim, child if it elaborates.

## Operating principles for slipbox cards
1. **One claim per card** — bundled claims are split candidates, but see (2) before splitting.
2. **Split only when it buys linkability** — if no future card would plausibly want to link to *part* of the current card, leave it whole. Long, single-claim cards are fine.
3. **Cards must stand alone** — if a card collapses without its source, it belongs back in `literature_notes/`. This is the same test as the tether check above, applied in reverse.
4. **Links must be conceptual, not topical** — sequential links (`t2 → t2a → t2b`) that mirror source order without a real conceptual relation are a smell.

## Granularity per layer
- **Reference note** → one source, verbatim. Mirrors the source's own structure; no reorganizing or atomizing.
- **Literature note** → one source, many bullets. Sized by source, not by claim — a class note with many bullet points is correct. Each bullet is an extraction candidate for potential promotion. Loosely one-idea-per-bullet aids later extraction, but it's a convenience, not a rule.
- **Slipbox card** → one claim. The only layer where single-claim discipline bites; promotion *is* the regrouping from source-shaped to claim-shaped.