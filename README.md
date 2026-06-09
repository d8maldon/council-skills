# council-skills

A Claude Code plugin marketplace with two plugins. Mythology-named so each
skill carries its own thematic role.

## 1. `pantheon` plugin (five-council audit protocol)

The divine assembly:

- **`athena`** -- currently-active mathematicians (Tao, Scholze, Bhargava,
  Huh, Viazovska, Venkatesh, Villani, Duminil-Copin, Figalli, Lurie) plus
  applied controls people (Annaswamy, Ames, Egerstedt, Tomlin, Krstic,
  Khalil, Hovakimyan). Goddess of wisdom + strategy.
- **`mnemosyne`** -- historical legends (Gauss, Riemann, Hilbert, Poincare,
  Cauchy, Weierstrass, Lebesgue, Banach, Kolmogorov, von Neumann, Klein,
  Noether) plus control-theory founders (Lyapunov, Krasovskii, LaSalle,
  Nagumo, Filippov, Moreau, Krasnoselskii, Tikhonov, Lefschetz, Popov,
  Kokotovic, Monopoli, Kalman, Pontryagin, Bellman, Wiener) plus
  estimation (Fisher, Cramer, Rao, Markov) plus ODE / functional analysis
  (Lipschitz, Picard, Kato, Fenchel). Titan goddess of memory, mother of
  the muses.
- **`hephaestus`** -- three-sweep engineering review by present-day
  authorities (Annaswamy, Lavretsky, Krstic, Slotine, Khalil, Ames, Tomlin,
  Belta, Egerstedt, Chuchu Fan, Asada, Hogan, Featherstone, Borrelli,
  Morari, Wise, Hovakimyan, Recht, Abbeel, Levine, Hespanha, Frazzoli,
  Boyd, Allgower, Mesbahi, Bertsekas). Master craftsman of Olympus.
- **`prometheus`** -- founders and modern leaders of AI / ML / CS (Turing,
  McCarthy, Minsky, Shannon, Rosenblatt, McCulloch & Pitts, Hebb, Samuel,
  Wiener, Pearl, Bayes, Fisher, Kolmogorov, Markov, Vapnik & Chervonenkis,
  Widrow, Ada Lovelace, Grace Hopper, Karen Sparck Jones, Barbara Liskov)
  plus the moderns (Hinton, LeCun, Bengio, Schmidhuber, He, Vaswani,
  Goodfellow, Sutton, Karpathy, Manning, Malik, Efros, Fei-Fei Li, Jordan,
  Valiant, Ghahramani, Bishop, Koller, Jeff Dean, Knuth, Lamport). Audits
  ML/CS work -- model choice, training & evaluation methodology,
  generalization, retrieval/ranking, algorithms, systems feasibility. Titan
  of forethought, the knowledge-bringer.
- **`hermes`** -- founders of vehicle dynamics (Olley, Milliken, Segel,
  Pacejka, Broulhiet, Lanchester, Ackermann/Lankensperger, Riekert &
  Schunck, Kane, Dubins, Reeds & Shepp, Dickmanns) plus the moderns
  (Gerdes, Rajamani, Guiggiani, Velenis, Borrelli, Thrun, Urmson, Kendall,
  Anguelov, Newey, Hrovat, Tseng). Audits vehicle-dynamics work -- tire
  models, load transfer, single-track / multibody plants, handling &
  stability, state & friction estimation, control allocation, racing lines,
  real-telemetry validation. God of roads, speed, and travelers.

All five enforce the **council-log protocol**: read
`notes/council-log.md` before any audit, classify each finding as
`NEW` / `RECURRING-UNFIXED` / `CONFLICT-WITH-PRIOR-SIGNOFF`, honour
prior pre-commitments, and apply the loop-break heuristic so iteration
actually converges.

## 2. `daedalus` plugin (CLAUDE.md behavioural guidelines for coding)

- **`tenets`** -- four principles for software-engineering tasks:
  1. think before coding (state assumptions, present multiple interpretations,
     ask when unclear),
  2. simplicity first (minimum code, no speculative features, no abstractions
     for single-use code),
  3. surgical changes (touch only what the request requires, match existing
     style, clean up only your own orphans),
  4. goal-driven execution (define verifiable success criteria so the loop
     can iterate independently).

  Named after the master craftsman of Greek mythology who knew when not to
  overcomplicate. Biases toward caution over speed.

  Distilled from
  [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills)
  (adapted into Claude Code plugin format). Original article:
  [AI Builder Club, "Karpathy's CLAUDE.md rules"](https://www.aibuilderclub.com/blog/karpathy-claude-md-rules).

## Install (Claude Code, any machine)

```
/plugin marketplace add d8maldon/council-skills
/plugin install pantheon@council-skills
/plugin install daedalus@council-skills
```

(Install either or both; they are independent.)

After install, the skills are available as slash commands:

- `/pantheon:athena`
- `/pantheon:mnemosyne`
- `/pantheon:hephaestus`
- `/pantheon:prometheus`
- `/pantheon:hermes`
- `/daedalus:tenets`

Or by description (Claude will auto-invoke when the user asks to
"audit the math", "consult athena", "consult mnemosyne", "consult
hephaestus", "consult prometheus" / "audit the ML", "consult hermes" /
"audit the vehicle dynamics", or when a coding task starts
in a fresh session and the daedalus tenets become relevant).

## Install (claude.ai web / desktop / mobile)

Upload `plugins/pantheon/skills/<skill-name>/` or
`plugins/daedalus/skills/<skill-name>/` as a Skill under
Settings -> Capabilities -> Skills on claude.ai. The same `SKILL.md`
format works.

## Local development

Clone, edit a `SKILL.md`, then on the test machine:

```
/plugin marketplace add file:///c/GIT/council-skills
/plugin install pantheon@council-skills
/plugin install daedalus@council-skills
```

## License

MIT.
