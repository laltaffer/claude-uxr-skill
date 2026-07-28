# Evidence Ladder — what a claim is allowed to rest on

Every claim in every /uxr artifact carries a tier tag. The tag is not decoration: it
decides what the claim may be used for downstream. **Strength order, strongest to
weakest: E1 > E2 > E3 > E4 > E5 > E0** — "weakest" always means toward E0, never the
numeral. A claim inherits the weakest tier in its load-bearing evidence chain.

## The tiers

- **E1 — Observed human behavior.** Analytics, session recordings, usability sessions,
  support tickets describing actual events, purchase/usage data. What people *did*.
- **E2 — Stated human attitude, first-party.** Interviews the operator ran, survey
  responses, direct user emails. What people *said to us*. (Say–do gap applies: E2
  about future behavior is weaker than E2 about past experience.)
- **E3 — Verbatim public VoC, sourced.** Forum posts, reviews, HN/Reddit threads,
  app-store reviews — exact words with links. What people *said in the wild*.
- **E4 — Desk research.** Published studies, industry surveys, competitor teardowns,
  analogous-domain findings. What's *known about people like ours*.
- **E5 — Synthetic panel output (grounded).** Panel runs whose personas meet
  synthetic-panel.md's grounding bar. Hypotheses with direction, never findings.
- **E0 — Assumption / model prior / ungrounded panel.** Intuition, unlabeled
  common sense, panels run on proto-personas. Must be flagged wherever it appears.

## Hard rules

1. **No promotion.** E5/E0 material never becomes "validated," "confirmed," or a
   "finding" — not by repetition, not by panel unanimity, not by pairing with E4. It
   graduates only by being *tested* at E1–E3, and the brief names that test.
   **Quarantine:** in every artifact, E5/E0 content appears only inside a section
   titled Hypotheses (or explicitly marked SYNTHETIC) — never interleaved with
   insights, however honestly tagged. Proximity is how leaks happen.
2. **Decision floors.** Go/no-go and validation decisions rest on E1–E3.
   Discovery questions ("what don't we know?", "what would surprise us?") may not be
   answered from E5/E0 at all — synthetic users cannot produce unknown unknowns about
   *our* users. Instrument design, hypothesis generation, and edge-case brainstorming
   are E5's home turf.
3. **The sycophancy discount.** Synthetic evidence is asymmetric: synthetic *praise*
   and synthetic *task success* are near-zero signal (models endorse concepts and push
   through friction real users won't — NN/g and Userbrain both demonstrated this);
   synthetic *confusion* about wording or structure is weak-but-real signal that the
   instrument or concept is ambiguous. Discount accordingly before anything reaches a
   brief. Suspicious unanimity across the panel is a variance-collapse tell, not
   consensus.
4. **Quotes.** Every quotation carries a source link (E2/E3) or the marker
   **[SYNTHETIC]** inline. A quote with neither does not ship. Paraphrases that could
   be mistaken for quotes get the same treatment.
5. **Mixed chains.** An insight built on E3 VoC *plus* panel elaboration is E5 unless
   the E3 alone supports it — write it both ways and keep the honest version.

## Persona provenance cards

Every persona ends with a `## Provenance` section: the corpus items it was composed
from (links/paths), the tier of each, coverage gaps, and a one-line grounding grade —
**grounded** (built from E1–E3 corpus) or **proto** (assumption document; title must
say so). Personas are evidence-bounded instruments, not characters.

## In the brief

The brief's insights section tags every claim inline — `[E3]`, `[E5]` — and closes
with two lines: *"This recommendation rests on: <tier + items>"* and *"What would
change the answer: <the E1–E3 test>."* If those two lines are hard to write, the
research isn't done.
