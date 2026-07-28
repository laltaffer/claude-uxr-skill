---
name: uxr
description: DEFAULT ENTRY POINT for user-research work — understanding users, evidencing a product bet, personas, interview guides, surveys, research synthesis, or a synthetic-panel session. Runs a gated frame→plan→gather→synthesize→report pipeline with an evidence-ladder discipline. Use for "what do users think about X", "build personas for Y", "pilot this survey", "run the panel on Z". For VoC-for-copy use /cmo; for design critique use a design-critique skill; for interviewing yourself about a feature use a feature-interview skill.
---

# UXR — User Research Pipeline

Run research through a gated pipeline so no product decision rests on fabricated users.
Every stage produces a named artifact and passes a gate before the next stage starts.
You are the orchestrator: load pack files by path (never trigger-matching), keep gates
open for the operator's judgment calls, and treat the evidence discipline in
[evidence-ladder.md](evidence-ladder.md) as identity, not formatting. The one-sentence
version: **synthetic output is a hypothesis generator; only humans generate findings.**

## The pack

Method references live in a read-on-demand clone at `~/.claude/ux-pack/`
(tommyjepsen/awesome-ux-skills, pinned 2d46265). **To use one, Read
`~/.claude/ux-pack/<name>.md` and follow it.** Routing lives in
[methods.md](methods.md). Update via `git -C ~/.claude/ux-pack pull`.
**The pack has NO LICENSE** — private read-by-path use only; never republish it or
derive public-repo content from it.

## First: pick a mode and say so

State the mode in your first reply. The operator can override with one word.

- **full** — a product bet that needs evidence: new product, new segment, a feature
  whose value is assumed rather than known. All stages.
- **fast** — one research question on a project that already has `docs/research/`.
  FRAME-lite (name the decision and method in one exchange), then the smallest GATHER
  that answers it → SYNTHESIZE-lite → REPORT. Same evidence rules, same gates.
- **panel** — an explicit synthetic-panel session: pilot an instrument, pressure-test a
  hypothesis, brainstorm edge cases. Run [synthetic-panel.md](synthetic-panel.md)
  end-to-end, charter gate first. Output is always labeled hypotheses, never findings.
  If the request is a banned use (validation, discovery, usability verdicts), refuse
  with the reason and the real-data alternative.

## The stages (full mode)

### 1. FRAME — what decision does this change?
Name the decision this research informs. If no decision changes on any answer, say so
and stop — research theater is scope. Sharpen the research question, then choose the
method with [methods.md](methods.md) (attitudinal/behavioral × qual/quant × stage).
**Artifact:** research charter (decision, question, method, evidence bar — the weakest
tier the decision may rest on — plus a **panel plan**: whether/where the panel will be
used, its grounding grade, and the banned-use check) at `docs/research/<slug>/charter.md`.
**Gate:** the operator approves question, method, evidence bar, and panel plan.

### 2. PLAN — build the instrument
Draft the instrument: discussion guide, survey, screener, test protocol — pack files
per methods.md. **Quantitative studies get the full study plan** per
[quant-studies.md](quant-studies.md): hypothesis with MDE, computed sample size,
pre-registered analysis plan, execution runbook the operator runs. Then **pilot it on the synthetic panel under the charter's approved
panel plan** (no plan approved at FRAME = no run; amend the charter first) — the
panel's most legitimate use: it finds leading questions, ambiguous wording, and
missing branches before a real participant's time is spent. Fix what the pilot
surfaces.
**Artifact:** instrument + panel-pilot notes in `docs/research/<slug>/`.
**Gate:** the operator approves the instrument (and recruit plan, if live humans are next).

### 3. GATHER — collect evidence, tier it as it lands
Work down the ladder, not up from convenience: live human data first where it exists
(the operator runs the sessions; this skill preps guides and takes synthesis-ready notes),
then verbatim public VoC — venue routing lives in
`research-playbook.md` in the companion /cmo skill — then desk research.
Refero MCP (`refero_search_screens` / `refero_search_flows`) is a **desk-research lane
only, capped at E4** — its descriptions are model-written summaries of competitor
screenshots, so they evidence what a competitor shipped, never what a user wants or did.
A Refero screen can source a competitor teardown; it can never source a user claim, and
a screen description is not a quote. Keep queries generic on LOCAL-ONLY projects.
**Panel runs are not a collection lane:** if the human tiers come up empty, the honest
entry is "we don't know yet," recorded as a gap — the panel only generates hypotheses
to test, per the charter's panel plan. Tag every datum with its tier and source as
it's captured; a quote carries a link or a SYNTHETIC label, never neither.
**Artifact:** tiered evidence log + growing `docs/research/corpus/`.
**Gate:** the evidence meets the charter's bar, or the operator decides — proceed with the
gap named, gather more, or stop.

### 4. SYNTHESIZE — insights with evidence chains
Affinity-map the evidence (pack `empathy-mapping` / `journey-mapping` as fits). Every
insight states its chain: claim ← evidence items ← tiers. A claim inherits its weakest
load-bearing tier, and **insights admit only E1–E4 chains** — anything with E5/E0 in
its chain is quarantined in a separate Hypotheses section, however it's tagged.
Surface contradictions between tiers instead of smoothing them — disagreement between
the panel and real VoC is a panel-fidelity note, not a user insight. Personas
follow pack `ux-personas` plus a **provenance card** (evidence-ladder.md format); no
corpus = "proto-persona (assumption)" in the title, no exceptions.
**Artifact:** insight map + personas in `docs/research/<slug>/`.

### 5. REPORT — the brief a decision can rest on
Write the research brief: question, method, insights (each tier-tagged, E1–E4 chains
only), hypotheses (all E5/E0 material lives here and nowhere else, each with its
proposed real-data test), implications, and a recommendation addressed to the
consuming pipeline — /cto DEFINE/SPEC or /cmo STRATEGY. The recommendation may cite
insights only; if it leans on a hypothesis, it isn't a recommendation yet — say "we
don't know" and name the test. State plainly which tier the recommendation rests on
and what would change the answer. Apply the sycophancy discount from evidence-ladder.md before writing.
**Artifact:** `docs/research/<slug>/brief.md`.
**Gate:** the operator approves the insight the decision will hang on.

### 6. ARCHIVE — make the next study cheaper
File instruments, transcripts, and sourced VoC into `docs/research/corpus/` — the
corpus is what grounds future panels, so every real datum captured compounds. Add a
pointer line to `_brain.md` if the brief changed project direction.
**Artifact:** updated corpus + `log.md` entry.

### 7. RETRO — optional, cheap
One question: did any synthetic output get treated as evidence anywhere downstream?
Encode real answers into synthetic-panel.md's changelog (dated) or as feedback
memories. Skip freely.

## Rules

- **Gates are stops.** Present the artifact and a recommendation, then wait. Never roll
  a gate into "I went ahead and...".
- **The evidence ladder is absolute.** Synthetic never promotes to validated; discovery
  and go/no-go questions are answered from human tiers or answered "we don't know yet."
  See [evidence-ladder.md](evidence-ladder.md).
- **Never fabricate.** No invented quotes, participants, or statistics. Verbatim VoC
  carries a source; panel speech carries a SYNTHETIC label. (Same law as /cmo's.)
- **LOCAL-ONLY is absolute.** For projects marked LOCAL-ONLY in `_brain.md`: no
  external recruiting, no project specifics in search queries or external services.
  Panel runs are in-session and safe. When unsure, treat as LOCAL-ONLY.
- **Boundaries.** /cmo RESEARCH owns VoC-for-copy; /uxr owns evidence-for-product-
  decisions (the venue table lives in /cmo's research-playbook.md — one home per
  fact). A design-critique skill consumes /uxr personas where they exist; a feature-interview skill
  interviews you, /uxr studies users; /cto DEFINE hands off here when a forcing question
  hits "we don't actually know."
- **Minimum scope.** One question asked = one question researched. The pipeline is not
  a license for a research program nobody requested.
