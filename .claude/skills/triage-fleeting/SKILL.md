---
name: triage-fleeting
description: Triage fleeting notes by lifecycle — recommend promote, merge, discard, or keep, flag stale captures, and catch source material misfiled into the inbox. Use when asked to triage, process, clear, or clean up fleeting notes or the inbox.
disable-model-invocation: true
user-invocable: true
argument-hint: "[path or glob; default fleeting_notes/]"
allowed-tools: Read, Grep, Glob
---

# triage-fleeting

Fleeting notes are **transient** — captured in the moment, meant to be processed (promoted, merged, or discarded) within days, not kept. This is **lifecycle triage** — deciding a note's next action — not a structural audit of note conventions. Read-only: recommend the next action; never move or delete files.

Fleeting notes hold **your own thoughts**; their normal promotion target is the **slipbox**. Source-derived material belongs in `literature_notes/` (own-words digests) or `references/` (verbatim) and should never have entered the inbox. So a source-tied capture found here is a **misfile** to be re-routed — not a normal promotion.

## Scope

- Default: `fleeting_notes/`. If `$ARGUMENTS` names a path/glob, use that.
- Staleness threshold: 7 days unless the conventions doc says otherwise.

## Per note

Determine age — use a frontmatter date if present, else file mtime. Then recommend **exactly one** next action — the *immediate* next step, not the note's only fate:

- **PROMOTE → slipbox candidate** *(normal path)* — a standalone claim in your own frame, statable independent of any source. Recommend drafting it as a slip note; say why it stands on its own.
- **MISFILE → literature note** *(recovery path)* — the capture is actually source-derived (a digest of, reaction to, or quote from something read) that landed in the inbox by mistake. It belongs in `literature_notes/`. Recommend re-routing it there and digesting in your own words; name the source if identifiable. This should be rare — a frequent occurrence means capture discipline is slipping upstream.
- **MERGE** — duplicates or extends another *fleeting* note → name the target. Fleeting ↔ fleeting only; never merge into a permanent note — folding content into a slip card is promotion, which you author.
- **DISCARD** — already captured downstream (a slip card, literature note, or reference), superseded, or a passing thought with no follow-up value. Checking the slipbox here is expected.
- **KEEP** — still genuinely in-flight → state why it isn't actionable yet.

**Bridge case — a fleeting note that relates to an existing slip card.** Comparison against the slipbox can only ever yield DISCARD or PROMOTE, never MERGE (nothing writes to the slipbox but you):

- duplicates an existing slip card → **DISCARD**.
- extends or refines one → **PROMOTE**, naming the card as link context (e.g. "extends [[x]] — fold in or write a linked slip, your call").

**Precedence — when more than one action's conditions hold.** They aren't competing; they're sequential stages. Apply this order and label the *highest-precedence applicable* action; note any downstream consequence in the reason:

```
route (MISFILE) → consolidate (MERGE) → dispose (PROMOTE | DISCARD | KEEP)
```

- **MISFILE** is highest — source material isn't a real fleeting note, so route it out before judging anything else.
- **MERGE** is next — consolidate overlapping captures before disposing; promotion or discard attaches to the *merged* result, never the fragment.
- **PROMOTE / DISCARD / KEEP** are terminal dispositions of a single, correctly-filed, consolidated note.

A note that both extends a peer and is slip-worthy reads as `MERGE`, with the slip candidacy flagged as what follows on the next pass.

Flag **OVERDUE**: older than the threshold and still unprocessed.

## Output

One line per note:

```
<file> — <age> — [PROMOTE→slipbox | MISFILE→literature | MERGE | DISCARD | KEEP] : <reason / target>
```

Then a summary:

- counts per action
- **misfile list** — captures that should be re-routed out of the inbox (watch this list; if it grows, source material is leaking into fleeting capture)
- **overdue list** — past threshold, still unprocessed

Recommend, don't act — you decide what actually moves, re-routes, or gets deleted.