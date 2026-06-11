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