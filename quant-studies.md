# Quant Studies — plans the operator executes

This file owns the quantitative lane: /uxr designs the study, the operator runs it, /uxr
analyzes what comes back. The spine is two disciplines: **sample sizes are computed in
code, never estimated**, and **the analysis plan is written before data exists**.
Qual heuristics stay in methods.md; evidence rules stay in evidence-ladder.md.

## Method by decision

| Decision looks like | Method | Evidence tier |
|---|---|---|
| Which pains/features matter most | MaxDiff (beats rating scales — no straight-lining) | E2 |
| Is this feature expected, delighting, or noise | Kano | E2 |
| Can people complete the core task; is v2 better | Unmoderated benchmark (success, time, SEQ) | E1/E2 |
| Does the navigation make sense | Card sort (15+) / tree test (30+) | E2 |
| How prevalent is a pain/behavior in the segment | Survey with quotas | E2 |
| What do people actually do in the product | Analytics/funnel (instrument via /cto first) | E1 |
| Which variant wins, live | A/B (needs traffic — check feasibility first) | E1 |
| What price range is tolerable | Van Westendorp (range-finding only, not demand sizing) | E2, weak |

Say-do applies: any survey about *future* behavior ("would you use/pay") is banned
phrasing — anchor to past behavior, or route the question to E1 methods.

## The study plan artifact

`docs/research/<slug>/study-plan.md` — the PLAN-stage artifact for quant work, gated
before execution. Every plan contains, in order:

1. **Decision + falsifiable hypothesis** — directional, with the *smallest difference
   that would change the decision* (the MDE). "H1: ≥40% of solo operators report
   setup-time as a top-2 pain; below 25% we drop the feature" — not "learn about
   pains."
2. **Population, sampling frame, recruitment reality** — who counts, where they're
   reachable, expected response rate. Recruitment is the binding constraint of a
   solo operation: if the computed n is unreachable, **shrink the question, never the
   power** — rank instead of size, benchmark instead of A/B, or re-scope to qual.
   Underpowered studies don't get run and reported with p-values.
3. **Instrument** — per survey-craft below; piloted on the synthetic panel for wording
   ambiguity only (panel outputs never inform expected effect sizes, base rates, or
   priors — that's E5 leaking into study design).
4. **Sample size, computed** — a script (Python: `statsmodels`/`scipy`) with alpha,
   power, effect size, and test named; script and output committed to
   `docs/research/<slug>/analysis/`. No n from memory, mine or the literature's.
5. **Pre-registered analysis plan** — exact tests, planned cuts, exclusion rules
   (speeders, straight-liners, failed attention checks), and what result triggers
   what decision. Written before data exists; anything else later is labeled
   exploratory.
6. **Execution runbook** — tool (Tally/Google Forms for surveys; Lyssna/Maze for
   unmoderated tests and sorts), distribution channels and copy, incentive, field
   window, and a day-2 quality check (drop-off point, garbage rate). Recruiting posts
   are outward-facing — the operator posts them. LOCAL-ONLY projects run no external
   studies, full stop.

## Survey craft — bias controls, non-negotiable

One construct per item; no double-barreled, leading, or loaded items. Balanced scales,
all points labeled, 5 or 7 points. Randomize option order and block order (LLMs and
humans both skew early-option). Screener separate from instrument, qualifying answers
not guessable. One attention check per ~15 items; ~3 minutes of stated length per 10
items. Demographics last. Behavioral anchors over hypotheticals throughout. NPS is a
tracking metric, not a research instrument — don't design studies around it.

## Sample-size quick anchors (still compute the real one)

- Margin of error on one proportion: ±10% ≈ n=96, ±5% ≈ n=384 (worst-case p=.5).
- Comparing two proportions at 80% power, α=.05: detecting 20-point gaps ≈ 90+/group;
  10-point gaps ≈ 390+/group — usually solo-infeasible; shrink the question.
- Task-success benchmarks: small-n is legitimate with adjusted-Wald CIs (n=20 gives
  ±~20%) — report the interval, not the point estimate.
- Card sort 15+, tree test 30+ per Nielsen/Baymard practice.

## Analysis — when the data comes back

Run the pre-registered plan in code (pandas/scipy/statsmodels), assumption checks
named in the script. Report effect sizes and CIs, not bare p-values. Apply the
pre-registered exclusions before looking at results. Un-pre-registered cuts are
labeled **exploratory** in the brief and generate hypotheses, not insights. Report
response rate, drop-off, and exclusion counts — a 12%-response-rate survey of a
self-selected forum is E2 with a named selection-bias caveat, and the brief says so.
Scripts, raw exports, and outputs live in `docs/research/<slug>/analysis/` (raw data
with PII stays local regardless of project remote policy).
