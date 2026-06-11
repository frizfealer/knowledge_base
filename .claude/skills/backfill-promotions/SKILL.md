---
name: backfill-promotions
description: Seed promotion markers on existing literature notes by proposing which bullets already became slip cards, for human confirmation before writing. Use when asked to backfill, seed, or reconstruct promotion links for the literature backlog written before the marker convention existed.
disable-model-invocation: true
user-invocable: true
argument-hint: "[literature note path or glob to backfill]"
allowed-tools: Read, Grep, Glob, Edit
---

# backfill-promotions

One-time seeding of promotion markers for literature notes written before the convention existed. Claude **proposes** bullet→card matches; the human **confirms**; only then are markers written. Claude never decides provenance on its own.

## Hard limit on inference — state both up front

Matching is semantic, not textual: promotion rewrites the bullet into the author's own frame, so a promoted bullet and its card usually share no strings.

- **Under-detection is expected and biased.** A well-reframed card may not resemble its source bullet at all → "no match found" does **not** mean "not promoted." The better the promotion, the more likely it's invisible here.
- **Topical overlap is not provenance.** A same-subject card is a *candidate to confirm*, never a confirmed match.

So: propose with low / medium / high confidence and a one-line rationale. Never assert a match.

## Procedure

1. Read the target literature note(s) and the slipbox.
2. For each **unmined** bullet (no `↑[[[`), find slip card(s) that plausibly are its promotion. Propose 0–2 candidates per bullet.
3. Present a numbered confirmation list:

   ```
   N. <note>: "<bullet snippet>"  →  [[[<id>]<title>]]   (confidence — why)
   ```

4. **Stop and wait.** The human replies with which proposals are correct (e.g. "accept 1, 4, 7").
5. For confirmed items **only**, append ` ↑[[[<id>]<title>]]` to the matching bullet line with Edit. Change nothing else. Report each line written.

## Rules

- Never write a marker that wasn't explicitly confirmed.
- Leave unconfirmed bullets unmarked — they flow to `/triage-literature` as backlog.
- Setting frontmatter `reviewed:` — only via the fully-mined proposal below. Backfilling some links is not the same as combing the note; partial coverage never closes a note.

## Fully-mined proposal

After writing confirmed markers, re-check each touched note. If **every** bullet in a note now carries a `↑[[[` marker (counting only confirmed markers, not pending proposals), the note has no uncombed remainder — it qualifies for closing. Then:

1. Present the note(s) for closing:

   ```
   <note> — <n>/<n> bullets mined → propose: reviewed: <today's date>
   ```

2. **Stop and wait** for explicit approval per note.
3. Set `reviewed:` only on approved notes. Notes with any unmarked bullet are never proposed — they stay open and flow to `/triage-literature`.