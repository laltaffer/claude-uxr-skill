# Methods — choosing one, and where the depth lives

This file routes; depth lives in the pack (`~/.claude/ux-pack/<name>.md`, read by
path) and in /cmo's venue table. Don't restate what those files own.

## Pick the method (Rohrer three-dimensional framework)

Locate the question on three axes, then the stage:

- **Attitudinal ↔ behavioral** — what people say vs. what they do. Say–do gap means
  behavioral beats attitudinal wherever the decision is about behavior.
- **Qualitative ↔ quantitative** — why/how (small-n, deep) vs. how-many/how-much
  (large-n, counts).
- **Context of use** — natural use, scripted tasks, abstracted concept, no product.

By stage: **strategize** (what to build) → interviews, field/forum immersion, diary
studies; **design** (make a flow work) → usability tests, card sorts, concept tests;
**assess** (did it work) → analytics, surveys, A/B.

Full landscape + tradeoffs: pack `ux-research-methods.md`.

## Pack routing

| Need | Read |
|---|---|
| Method selection depth | `ux-research-methods.md` |
| Personas from data | `ux-personas.md` (+ provenance card, evidence-ladder.md) |
| Says/thinks/does/feels synthesis | `empathy-mapping.md` |
| Journey/timeline synthesis | `journey-mapping.md` |
| Concept storyboards | `ux-storyboard.md` |
| Divergence/convergence framing | `double-diamond.md` |
| Heuristic review vocabulary | `ux-heuristics-review.md` (note: a design-critique skill owns design review) |

## Solo-operator reality — methods one person can actually run

- **VoC mining** (E3): the workhorse. Venue routing lives in
  `research-playbook.md` in the companion /cmo skill — same two laws (never
  fabricate/paraphrase quotes into existence, read-only accounts).
- **Own-network interviews** (E2): reach the audiences you already have access to;
  niche audiences via forums and community guides. 5–8 interviews per
  question; recruit screener piloted on the panel first.
- **Guerrilla/unmoderated tests** (E1): once there's a build — watch 5 people try the
  core task. Five users find most of what's findable per round; more rounds beat
  bigger rounds.
- **Product analytics + support inbox** (E1): shipped projects only. Instrument before
  the question arrives.
- **Paid AI-moderated platforms** (Outset, Listen Labs, Strella, Maze AI Moderator):
  real humans, AI interviewer — legitimate E2 at scale. Optional spend; propose only
  when a decision justifies it. Never LOCAL-ONLY projects.

## Sample-size heuristics (qual)

Qual usability: ~5 users/round; more rounds beat bigger rounds. Interviews: to
saturation, usually 5–8 per segment. Say which regime a number came from when
reporting. **Everything quantitative** — method-by-decision table, computed sample
sizes, survey craft, pre-registered analysis — lives in
[quant-studies.md](quant-studies.md).
