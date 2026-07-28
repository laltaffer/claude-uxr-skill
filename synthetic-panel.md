# Synthetic Panel — protocol and guardrails

A panel is N independent, corpus-grounded personas answering an instrument. It is a
hypothesis generator with a documented failure signature: collapsed variance,
sycophancy, caricature, friction-blindness. This file exists so we harvest the value
and never mistake the output for research. It is a **living file** — the science moves
fast; append dated entries to the changelog when new fidelity evidence crosses your
path.

## Allowed and banned uses

**Allowed:** piloting instruments (guides, surveys, screeners — the most-endorsed use
in the field), hypothesis generation before real research, edge-case and objection
brainstorming, red-teaming a concept's framing, re-interrogating an existing corpus
("what would the corpus predict about X?"). The boundary with banned discovery:
brainstorming produces **questions to take to real data** ("do users hit this case?
go check"), never claims that users have them. If the output would be phrased as a
statement about our users rather than a to-verify item, it's discovery — banned.

**Banned:** validation or go/no-go verdicts; discovery of unknown unknowns; usability
findings (synthetic users do not experience friction — they push through walls real
users stop at); representing niche or marginalized populations we have no corpus for
(caricature/flattening risk is highest exactly there); anything reported downstream
without its SYNTHETIC label. A banned-use request gets a refusal, the reason, and the
real-data alternative.

## Charter first (the panel's gate)

Before any run, a charter must be approved: the question, the banned-use check, the
grounding sources to be used, N, and what will be done with the output. In pipeline
runs (full/fast), the FRAME charter's **panel plan** block is this charter — a run
outside the approved plan means amending the charter first, not running quietly. In
panel mode, write the charter standalone and gate on it. Panels are cheap; ungoverned
panels are how E5 leaks into decisions.

## Grounding protocol

- **Personas are composed from the project's corpus** (`docs/research/corpus/` —
  sourced VoC, transcripts, reviews, support threads), written as first-person
  backstories stitched from real fragments. Richer idiographic grounding measurably
  beats category labels (Stanford 2024: interview-grounded 85% vs demographics-only
  74% of test-retest ceiling). Connective tissue between fragments is kept minimal,
  and any backstory statement not traceable to a corpus item is an invention — the
  provenance card lists it under "invented connective detail" so grounded fragments
  and glue never blur.
- **Grounding floor:** a persona counts as grounded only if its card cites **≥3
  independent corpus items from ≥2 venues** covering its core cluster (behaviors and
  pains, not just demographics), recency noted. Below the floor it's a proto-persona.
- **Naked demographic conditioning is banned.** "You are a 34-year-old rural homeowner"
  produces out-group caricature and variance collapse (CoMPosT EMNLP 2023; Nature MI
  2025; Bisbee 2024). Demographics may appear only as facts inside a corpus-derived
  backstory.
- **Grounding grade decides the tier:** corpus-grounded panel → E5; thin/no corpus →
  proto-personas, output is E0 and the charter must say so before the run.

## Panel mechanics

- **N = 5–7 distinct personas** covering different corpus clusters, not variations of
  one archetype.
- **Independence is the point:** dispatch one subagent per persona, context containing
  only that persona's card and the instrument — never other personas' answers, never
  the surrounding conversation's hopes for the product. Cross-contamination
  manufactures consensus.
- **Order-randomize** option lists per persona (LLM answers skew to early options —
  NeurIPS 2024).
- **Elicit distributions, not modes:** for closed questions, each persona gives a
  verbalized distribution ("60% likely I'd…, 25%…") rather than one answer — a
  training-free diversity technique (Verbalized Sampling, arXiv:2510.01171). The
  numbers are a diversity elicitation, not calibrated probabilities: report them as
  qualitative spread and lean, and never let synthetic percentages reach a brief.
- **Interviewer posture inside the run:** non-leading probes, five-whys on the past
  ("tell me about the last time…"), never "would you use/pay for…" — synthetic users
  answer hypotheticals even more agreeably than humans do.

## Reading the output

- Report **spread, not means**. Disagreement between personas is the interesting
  signal; unanimity is a variance-collapse tell and gets flagged, not celebrated.
- Apply the **sycophancy discount** (evidence-ladder.md): synthetic praise and task
  success ≈ noise; synthetic confusion about wording/structure = weak-real signal.
- Panel-vs-corpus contradictions are panel-fidelity notes (never call them findings)
  — log them in the changelog; they don't enter briefs as user claims.
- **Output format:** the report leads with the header `SYNTHETIC PANEL — hypotheses,
  not findings`, and every hypothesis ships with its proposed E1–E3 test.

## Changelog

- **2026-07-09b** — cross-model hardening pass (10 findings, all applied): panel charter
  unified with FRAME's panel-plan block (closed the pipeline bypass); E5/E0 quarantine
  to Hypotheses sections; explicit tier strength ordering; grounding floor (≥3 items,
  ≥2 venues); invented-connective-detail disclosure; GATHER sufficiency gate;
  brainstorm-vs-discovery boundary; panel-not-a-collection-lane; "findings about the
  panel" → panel-fidelity notes; verbalized-sampling numbers demoted to qualitative
  spread.
- **2026-07-09** — File created. Baseline positions from the mid-2026 literature sweep
  (see repo `docs/synthetic-uxr-landscape.md`): grounded-twin ceiling ~85% of human
  test-retest on *survey attitudes only* (Stanford, arXiv:2411.10109); 182-study
  review found no prompting technique reaches human fidelity; field consensus =
  piloting/hypothesis yes, validation/discovery/usability no.
