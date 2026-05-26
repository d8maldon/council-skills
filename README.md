# council-skills

A Claude Code plugin marketplace that ships the three-council audit
protocol used in analytical research:

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

## Install (Claude Code, any machine)

```
/plugin marketplace add d8maldon/council-skills
/plugin install council@council-skills
```

After install, the three skills are available as:

- `/council:math-god-mode`
- `/council:og-math-experts`
- `/council:controls-expert-reviewer`

Or by description (Claude will auto-invoke when the user asks to
"audit the math", "consult the OGs", "controls expert review", etc.).

## Install (claude.ai web / desktop / mobile)

Upload `plugins/council/skills/<skill-name>/` as a Skill under
Settings → Capabilities → Skills on claude.ai. The same `SKILL.md`
format works.

## Local development

Clone, edit a `SKILL.md`, then on the test machine:

```
/plugin marketplace add file:///c/GIT/council-skills
/plugin install council@council-skills
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
