# /uxr — a gated user-research pipeline skill for Claude Code

A Claude Code skill that runs user research through a gated pipeline so no product
decision rests on fabricated users: FRAME → PLAN → GATHER → SYNTHESIZE → REPORT →
ARCHIVE → RETRO. Every stage produces a named artifact and stops at a gate for your
judgment. Three modes: **full** (a product bet that needs evidence), **fast** (one
question on a project that already has research), **panel** (an explicit synthetic-panel
session).

The point of the skill is the discipline, not the templates. Two things carry it:

- **[evidence-ladder.md](evidence-ladder.md)** — every claim carries a tier tag
  (E1 observed behavior → E0 assumption), a claim inherits the weakest tier in its
  chain, and synthetic output never promotes to validated. Go/no-go decisions rest on
  E1–E3 or the honest answer is "we don't know yet."
- **[synthetic-panel.md](synthetic-panel.md)** — synthetic personas are a hypothesis
  generator, never a findings generator. The panel's legitimate jobs are piloting
  instruments, generating hypotheses, and brainstorming edge cases. Validation,
  discovery, and usability verdicts are refused with the reason and the real-data
  alternative.

The evidence base for that stance is in
[docs/synthetic-uxr-landscape.md](docs/synthetic-uxr-landscape.md) — a cited survey of
the academic and practitioner literature on synthetic users as of mid-2026.

Built for a solo founder / one-person company working with Claude Code as the research
team.

## Install

```bash
git clone https://github.com/laltaffer/claude-uxr-skill.git ~/.claude/skills/uxr
```

New Claude Code sessions will pick it up as `/uxr`.

## What it expects

- **Method references from
  [tommyjepsen/awesome-ux-skills](https://github.com/tommyjepsen/awesome-ux-skills)** —
  clone it to `~/.claude/ux-pack/` and the skill reads files from it by path.
  `methods.md` routes to the ones it uses. **That repo carries no license** — clone it
  for your own use, don't republish it or derive public content from it. The pipeline
  degrades gracefully if you skip the pack and run the stages inline.
- **A per-project memory file** (`_brain.md` here — rename to your convention) and a
  `docs/research/` directory per project for charters, instruments, and briefs.
- Optional: the companion [/cmo skill](https://github.com/laltaffer/claude-cmo-skill).
  GATHER routes VoC venue selection to its `research-playbook.md`, and REPORT can
  address its STRATEGY stage. Optional: the companion
  [/cto skill](https://github.com/laltaffer/claude-cto-skill), whose DEFINE stage hands
  off here when a forcing question hits "we don't actually know."
- Optional: the [Refero](https://refero.design) MCP server, used in GATHER as a
  desk-research lane capped at E4 — competitor artifacts, never user evidence.

## Customize

- `methods.md` — the "Solo-operator reality" section lists the methods one person can
  actually run; edit it to the audiences and channels you actually have.
- `quant-studies.md` — sample-size and MDE machinery for the quantitative lane; assumes
  you execute the study yourself.
- `evidence-ladder.md` — if you adopt different tier names, change them here; every
  other file defers to this one.

## License

MIT.
