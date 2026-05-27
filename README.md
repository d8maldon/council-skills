# council-skills

A Claude Code plugin marketplace with two plugins.

## 1. `council` plugin (three-council audit protocol for analytical research)

- **`math-god-mode`** - currently-active mathematicians (Tao, Scholze,
  Bhargava, Huh, Viazovska, Venkatesh, Villani, Duminil-Copin, Figalli,
  Lurie) plus applied controls people (Annaswamy, Ames, Egerstedt, Tomlin,
  Krstic, Khalil, Hovakimyan).
- **`og-math-experts`** - historical legends (Gauss, Riemann, Hilbert,
  Poincare, Cauchy, Weierstrass, Lebesgue, Banach, Kolmogorov, von Neumann,
  Klein, Noether) plus control-theory founders (Lyapunov, Krasovskii,
  LaSalle, Nagumo, Filippov, Moreau, Krasnoselskii, Tikhonov, Lefschetz,
  Popov, Kokotovic, Monopoli, Kalman, Pontryagin, Bellman, Wiener) plus
  estimation (Fisher, Cramer, Rao, Markov) plus ODE / functional analysis
  (Lipschitz, Picard, Kato, Fenchel).
- **`controls-expert-reviewer`** - three-sweep engineering review by
  present-day authorities (Annaswamy, Lavretsky, Krstic, Slotine, Khalil,
  Ames, Tomlin, Belta, Egerstedt, Chuchu Fan, Asada, Hogan, Featherstone,
  Borrelli, Morari, Wise, Hovakimyan, Recht, Abbeel, Levine, Hespanha,
  Frazzoli, Boyd, Allgower, Mesbahi, Bertsekas).

All three enforce the **council-log protocol**: read
`notes/council-log.md` before any audit, classify each finding as
`NEW` / `RECURRING-UNFIXED` / `CONFLICT-WITH-PRIOR-SIGNOFF`, honour
prior pre-commitments, and apply the loop-break heuristic so iteration
actually converges.

## 2. `karpathy-rules` plugin (CLAUDE.md behavioural guidelines)

- **`karpathy-claude-md`** - four principles for software-engineering
  tasks: (1) think before coding (state assumptions, present multiple
  interpretations, ask when unclear), (2) simplicity first (minimum code,
  no speculative features, no abstractions for single-use code), (3)
  surgical changes (touch only what the request requires, match existing
  style, clean up only your own orphans), (4) goal-driven execution
  (define verifiable success criteria so the loop can iterate
  independently). Biases toward caution over speed.

Distilled from [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills)
(adapted into Claude Code plugin format). Original article:
[AI Builder Club, "Karpathy's CLAUDE.md rules"](https://www.aibuilderclub.com/blog/karpathy-claude-md-rules).

## Install (Claude Code, any machine)

```
/plugin marketplace add d8maldon/council-skills
/plugin install council@council-skills
/plugin install karpathy-rules@council-skills
```

(Install either or both; they are independent.)

After install, the skills are available as slash commands:

- `/council:math-god-mode`
- `/council:og-math-experts`
- `/council:controls-expert-reviewer`
- `/karpathy-rules:karpathy-claude-md`

Or by description (Claude will auto-invoke when the user asks to
"audit the math", "consult the OGs", "controls expert review", or
when a coding task starts in a fresh session).

## Install (claude.ai web / desktop / mobile)

Upload `plugins/council/skills/<skill-name>/` or
`plugins/karpathy-rules/skills/<skill-name>/` as a Skill under
Settings -> Capabilities -> Skills on claude.ai. The same `SKILL.md`
format works.

## Local development

Clone, edit a `SKILL.md`, then on the test machine:

```
/plugin marketplace add file:///c/GIT/council-skills
/plugin install council@council-skills
/plugin install karpathy-rules@council-skills
```

## Origin

Distilled from the multi-pass council protocol used in the
[Multi-Agent-CBF](https://github.com/d8maldon/Multi-Agent-CBF) research
project. See its `notes/SESSION_HANDOFF.md` §3 for the historical context
and §3.2 for the protocol rationale (Pass 13 found a paper-internal bound
mismatch in 12 ms that 12 prior passes had missed; Passes 43-49 surfaced a
recurring relative-degree-drop pattern that triggered the Pass-52 plant
switch).

## License

MIT.
