# Promotion tracking (literature → slipbox)

Two markers record extraction state on literature notes. You add them **at promotion time**, never retroactively required. Together they separate two different questions: _what came out of a note_ (per-bullet) and _whether the note has been fully combed_ (note-level).

## 1. Per-bullet promotion link

When a literature-note bullet becomes a slip card, append a backlink to that bullet, prefixed with `↑` ("promoted up to the slipbox"):

```
- Sutton & Barto define the return as the discounted sum of future rewards ↑[[[t2c]discounting makes value functions converge]]
```

Multiple cards → multiple `↑` links on the line. The `↑` sigil distinguishes a _provenance_ link from an ordinary see-also wikilink.

- A bullet is **mined** iff its line contains `↑[[[`.

## 2. Note-level review status

Once you've combed the whole note and decided what promotes, add to its frontmatter:

```
reviewed: 2026-06-09
```

Absence means the note hasn't been fully combed — its unlinked bullets are **backlog**, not deliberate skips.

## Derived states (used by `/triage-literature`)

|state|`reviewed`?|mined bullets?|meaning|
|---|---|---|---|
|untouched|no|none|never combed|
|in progress|no|some|started, not finished|
|closed|yes|any|combed; unlinked bullets = deliberate non-candidates|
|dormant|no|(any)|no `reviewed` and older than the staleness threshold → unmined and aging. A prompt to consider mining, **never** to discard — resting indefinitely is fine, and a long-dormant note is a candidate for the wiki layer, not the bin.|

Staleness threshold: 4 weeks unless overridden here.

Only count unlinked bullets as backlog in **untouched** / **in-progress** notes. In a **closed** note, an unlinked bullet is a non-candidate, not unfinished work.

Literature notes are a standing record and are **never discarded** by triage — that's a fleeting-note outcome, not a literature-note one. A `dormant` note is surfaced for awareness only.

# Hypothesis resolution (hypotheses → literature or slipbox)

Hypotheses live in `hypotheses/` as human-authored bets that aren't yet earned. Resolving one does **not** send it to a fixed destination. A resolved hypothesis produces a _finding_; the finding re-enters the ordinary pipeline at whatever layer its generality warrants, decided by the **same tether test** used everywhere — strip the test apparatus, does the claim still stand?

## Status lifecycle

`status:` frontmatter drives the layer. Only `proposed` / `testing` are resident — on resolution the note transforms into a layer below.

|status|meaning|on resolution|
|---|---|---|
|proposed|written down, untested|—|
|testing|actively being evaluated|—|
|confirmed / refuted|resolved|route the finding by the tether test (below)|

A hypothesis is never itself a standing record — that's a literature-note property, not a hypothesis-note one.

## Routing the finding — no default either way

Run the tether test on the **claim you've earned**, not on the method. An empirical test routinely earns a context-free claim — usually that's why you ran it. A _single_ test rarely licenses a universal, so first confirmations often land context-bound and promote later; that's the normal lifecycle, not a default toward either layer.

**Context-free finding → slipbox, transform-in-place.** The hypothesis _is_ the claim, now earned. Move into `slipbox/`, assign a Luhmann ID by its conceptual neighbour, rewrite the title to claim form, strip the test scaffolding (R4 / the stand-alone test). Trace: `origin: hypothesis` and `tested: <date>`, frontmatter bookkeeping next to `title:` — not part of the claim. No `↑[[[…]]]` marker; nothing is left behind to point from.

**Context-bound finding → literature note, transform-in-place.** The result leans on its conditions ("co-movement beat level on this universe, on metric M"), so the experiment is its tether — and the note is a genuine standing record. Move into `literature_notes/`, reframe as the digested result-in-context (the old `## Status notes` test log is its body), and mark `origin: hypothesis` to distinguish a result earned by testing from a digest of someone else's source. From here the ordinary literature → slipbox promotion applies: a context-free claim cut from it later spawns a slip card with the normal `↑[[[…]]]` marker (keep-both, because the literature note persists).

**Uninformative null → discard.** The rare exit. Most negative results are themselves context-bound findings ("co-movement did _not_ help, under conditions C") and become literature notes like any other.