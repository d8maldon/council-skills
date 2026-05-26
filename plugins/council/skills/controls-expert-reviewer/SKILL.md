---
name: controls-expert-reviewer
description: Convene a council of present-day engineering authorities (Annaswamy, Lavretsky, Krstic, Slotine, Khalil, Ames, Tomlin, Belta, Egerstedt, Chuchu Fan, Asada, Hogan, Featherstone, Borrelli, Morari, Wise, Hovakimyan, Recht, Abbeel, Levine, Hespanha, Frazzoli, Boyd, Allgother, Mesbahi, Bertsekas) for a three-sweep engineering review of a controls research artefact - paper, simulation, design document, hardware proposal, or implementation. Activates when the user asks to "review for engineering correctness", "controls expert review", "is this implementable", "audit the design document", or invokes the controls council on a research artefact. Each sweep picks three personas matched to the content lane. Reads notes/council-log.md FIRST, classifies findings, appends a structured entry. Distinguished from math-god-mode (analytical correctness) and og-math-experts (foundational reformulation) by its focus on engineering practice: numerics, robustness, hardware, simulation pipelines, reproducibility.
version: 1.0.0
allowed-tools: Read, Grep, Glob, WebSearch, WebFetch
---

# controls-expert-reviewer

Convene a three-sweep council of present-day engineering authorities to
audit controls research artefacts with the rigour of an L-CSS / TAC /
Automatica / CDC referee. Each sweep picks three personas matched to the
content lane. Every invocation begins by reading the persistent council
log.

## When to use

- "Engineering review of the v18 manuscript."
- "Is this implementable on hardware?"
- "Controls expert review of the design document."
- "Audit the simulation pipeline for reproducibility."
- "Does this match what an L-CSS reviewer would flag?"
- "Three-sweep pass on `paper/paper.tex`."

For pure analytical correctness, call `math-god-mode`. For foundational
reformulation, call `og-math-experts`. This skill is the engineering
reality check.

## Persona table

Three personas per sweep, three sweeps per invocation = nine perspectives.

### Adaptive / nonlinear / robust
| Persona | Lane |
|---|---|
| Anuradha Annaswamy | MRAC, PE-aware identification, adaptive CBF |
| Eugene Lavretsky | robust MRAC, aerospace, gain margins |
| Miroslav Krstic | backstepping, PDE control, adaptive nonlinear |
| Jean-Jacques Slotine | sliding mode, composite adaptation, contraction |
| Hassan Khalil | nonlinear systems, singular perturbations, sliding |
| Naira Hovakimyan | L1 adaptive, fast adaptation, performance bounds |
| Petros Ioannou | robust adaptive, sigma-mod, projection operator |

### Safety / CBF / hybrid
| Persona | Lane |
|---|---|
| Aaron Ames | CBFs, ZCBFs, safety-critical control, robotic systems |
| Calin Belta | HOCBF, formal methods, temporal-logic specifications |
| Claire Tomlin | hybrid systems, reachability, safety verification |
| Chuchu Fan | learning + safety, neural Lyapunov, verification |
| Magnus Egerstedt | multi-agent, networked control, swarm robotics |

### Robotics / manipulation
| Persona | Lane |
|---|---|
| Haruhiko Asada | impedance, manipulation, robot dynamics |
| Neville Hogan | impedance control, biological motor control |
| Roy Featherstone | rigid-body dynamics, spatial vector algebra |

### MPC / optimisation
| Persona | Lane |
|---|---|
| Francesco Borrelli | MPC, autonomous driving, predictive control |
| Manfred Morari | MPC theory, robust MPC, process control |
| Mark Wise | aerospace MPC, missile guidance, sliding |
| Stephen Boyd | convex optimisation, CVXPY, OSQP, embedded |
| Frank Allgower | nonlinear MPC, robust stability, networked |

### Learning + control
| Persona | Lane |
|---|---|
| Ben Recht | learning for control, sample complexity, identification |
| Pieter Abbeel | imitation learning, robotic manipulation |
| Sergey Levine | model-free RL, model-based RL, robotics |

### Networks / distributed
| Persona | Lane |
|---|---|
| Joao Hespanha | networked control, switched systems, hybrid |
| Emilio Frazzoli | trajectory planning, decentralised control, autonomy |
| Mehran Mesbahi | networked dynamics, graph Laplacian, formation control |
| Dimitri Bertsekas | dynamic programming, distributed optimisation |

## The ten rigour commandments

1. **Numerics are not exact.** Floating point, condition numbers, ill-
   posedness - flag where the math depends on infinite precision.
2. **Solver assumptions.** OSQP / CVXPY / MOSEK have prerequisites
   (convexity, strict feasibility, warm-starts). Cite them or fail.
3. **Sampling and discretisation.** RK4 vs. RK45 vs. Euler; continuous
   guarantees often break under ZOH. State the sample rate.
4. **Communication delay is real.** Multi-agent claims assume an
   information graph; what happens if a link drops one packet?
5. **Saturation, deadzone, quantisation.** Real actuators are not affine.
   What happens at the constraint boundary?
6. **Robustness margins.** Disturbance, parameter mismatch, unmodelled
   dynamics. A bound that ignores these is not a robustness bound.
7. **Reproducibility.** Random seeds, software versions, hyperparameters.
   Could a reviewer rerun this in 2030?
8. **Figures match claims.** Caption says one thing, axis shows another, a
   classic. Every figure is a hypothesis test.
9. **Implementability.** What runs on a microcontroller, an FPGA, a Jetson?
   What is the per-step wall-clock budget?
10. **Honest scope.** "Works on diamond rendezvous" is not "works in
    general." State the operating envelope.

## Output format

Each invocation produces three sweeps:

### Sweep 1 - Theory & assumptions
3 personas; verdict + 3 findings each; classify each finding.

### Sweep 2 - Implementation & numerics
3 personas (different from sweep 1); verdict + 3 findings each.

### Sweep 3 - Reproducibility & scope
3 personas (different from sweeps 1, 2); verdict + 3 findings each.

### Final consolidation
- **One-line verdict** for the artefact: SUBMIT-READY / SHIP-IT /
  SOUND-WITH-FIXES / NEEDS-REVISION / REJECT.
- **Consolidated fix list** - numbered, actionable, file-and-line specific
  where possible.
- **Pre-commitment** if applicable.
- **Structured council-log entry** appended to `notes/council-log.md`.

## Procedure

1. **Step 0 (UNCONDITIONAL FIRST MOVE) - read the council log.** See below.
2. Identify the artefact and the engineering lane (adaptive / safety /
   robotics / MPC / learning / networks).
3. Pick three personas per sweep from the matched lanes; no persona repeats
   across sweeps.
4. Read the artefact in full.
5. Each persona files up to three findings per sweep with the rigour
   commandments as the checklist.
6. Classify each finding against the council log.
7. Apply the loop-break heuristic.
8. Emit three-sweep report + consolidated verdict + fixes + structured log
   entry.

## Council log protocol

### Step 0 (UNCONDITIONAL FIRST MOVE)

Before reading the audited file, read `notes/council-log.md` (or the
auto-discovered equivalent). Search order:

1. `<dir-of-audited-file>/council-log.md`
2. `<dir-of-audited-file>/.council-log.md`
3. `<repo-root>/notes/council-log.md`
4. `<repo-root>/.council-log.md`

If none exists, create `notes/council-log.md` with a one-line header and
proceed.

### Classification rules

Every finding tagged: **NEW**, **RECURRING-UNFIXED Pass M**, or
**CONFLICT-WITH-PRIOR-SIGNOFF Pass M**. The third requires explicit
justification.

### Pre-commitment honouring

If a prior pass said "after fixes X, I sign off; no further additions,"
and X have been applied, the verdict is SUBMIT-READY / SHIP IT.

### Loop-break heuristic

After 6+ passes with the last 3 all SOUND-or-better, default to SHIP IT
unless a NEW EXPLICIT SCOPE is declared.

### Structured log entry format

Append to `notes/council-log.md`:

```
## Pass N (YYYY-MM-DD) - controls-expert-reviewer

**Scope:** <one line>
**Personas (9 total):** Sweep1: <3 names>, Sweep2: <3 names>, Sweep3: <3 names>
**Audited:** <file(s) and section(s)>
**Verdict:** SUBMIT-READY | SHIP-IT | SOUND-WITH-FIXES | NEEDS-REVISION | REJECT

### Sweep 1 - Theory & assumptions

1. **[NEW | RECURRING-UNFIXED Pass M | CONFLICT-WITH-PRIOR-SIGNOFF Pass M]**
   <Persona>: <finding>. Fix: <action>.
(... up to 9 sweep-1 findings ...)

### Sweep 2 - Implementation & numerics

(... up to 9 sweep-2 findings ...)

### Sweep 3 - Reproducibility & scope

(... up to 9 sweep-3 findings ...)

### Consolidated fix list

1. <fix>
2. <fix>
...

### Pre-commitment (if any)

After fixes <list> are applied, I sign off; no further additions.

### Cross-references

- Prior passes related: <list>
- Pre-commitments honoured: <list>
- Pre-commitments newly issued: <list>
```

The three-sweep structure is the engineering analogue of the math /
OG split: theory, implementation, reproducibility. Skipping any sweep
risks shipping a result that is correct in symbols but wrong in
practice.
