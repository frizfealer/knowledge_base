# knowledge_base

My knowledge base with slipbox organization. Follows Ahrens (*How to Take Smart Notes*): **fleeting → literature → permanent (slipbox)**.

## Structure

```
fleeting_notes/    Raw, unprocessed captures
literature_notes/  Digested notes tethered to a source
slipbox/           Permanent notes (Zettelkasten) — the network I think with
hypotheses/        Open bets I'm testing — a parallel human-authored feeder into slipbox
Templates/         Reusable note skeletons used when creating new notes
```

## Note types

### Fleeting note
A raw, in-the-moment capture — a thought, observation, or question jotted down before it disappears. Fleeting notes are temporary: they exist to be processed (promoted, merged, or discarded) within days, not kept forever. No structure or sourcing requirements.

### Literature note
A digested note about what a specific source (book, paper, lecture, article, course chapter) said, written in my own words and tethered to that source. **Tethered** means the note's framing leans on knowing where the idea came from — references like "the paper argues…" or "Ch. 3 introduces…" carry the weight. The operational test: *if I deleted the source attribution, would the note still stand?* If no, it's a literature note.

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

### Hypothesis note
An open bet I want to test — a proposed idea whose truth I don't yet know ("does modeling bond similarity by *co-movement* beat our current *same-level* assumption?"). Human-authored like the slipbox, but **not yet earned**: it asserts nothing I'd defend, only something worth testing. That epistemic status is exactly why it can't live in the slipbox, which is for claims I've earned. (In the authorship/epistemics grid: slipbox = human + earned; the wiki layer = AI + encountered; a hypothesis = human + *not-yet-earned*.)

Lives in `hypotheses/` with a `status:` field: `proposed` → `testing` → `confirmed` / `refuted`. Resolving a hypothesis doesn't send it to a fixed layer — it produces a *finding*, and the finding re-enters the ordinary pipeline at whatever layer its generality warrants, by the **same tether test** I apply to everything else (strip the test apparatus; does the claim still stand?). The folder is pure staging: every note eventually leaves it, either transformed into a note in another layer or — rarely — discarded as an uninformative null. So unlike a literature note (a permanent record), a hypothesis is transient, closer to a fleeting note in lifecycle, just on a longer clock.

**Routing, no default either way.** Run the tether test on the *claim I've earned*, not on the method — an empirical test routinely earns a context-free claim, which is usually why I ran it. A single test rarely licenses a universal, so first confirmations often land context-bound and promote later; that's the normal lifecycle, not a lean toward either layer.

- **Context-free finding → slipbox, transform-in-place.** The hypothesis *is* the claim, now earned. Move into `slipbox/`, assign a Luhmann ID, rewrite the title to claim form, strip the test scaffolding. Trace `origin: hypothesis` + `tested: <date>`; no `↑[[[…]]]` marker, since nothing is left behind to point from.
- **Context-bound finding → literature note**, tethered to the experiment as its source ("co-movement beat level on this universe, on metric M"). Move into `literature_notes/`, mark `origin: hypothesis` to flag a result I earned by testing rather than a digest of someone else's source. From there the ordinary literature → slipbox promotion takes over: a context-free claim cut from it later spawns a slip card with the normal `↑[[[…]]]` marker.

## Operating principles for slipbox cards

1. **One claim per card** — bundled claims are split candidates, but see (2) before splitting.
2. **Split only when it buys linkability** — if no future card would plausibly want to link to *part* of the current card, leave it whole. Long, single-claim cards are fine.
3. **Cards must stand alone** — if a card collapses without its source, it belongs back in `literature_notes/`. This is the same test as the tether check above, applied in reverse.
4. **Links must be conceptual, not topical** — sequential links (`t2 → t2a → t2b`) that mirror source order without a real conceptual relation are a smell.