# embraOS-QNM-Core: The Conserved Epoch

> **A note on register.** This derivation separates its *operational core* from its *motivation*,
> exactly as `README.md` does — and it describes a system that **runs**: embraOS-QNM-Core (v0.5.0,
> 2026-08-27), a custom **non-LLM** core built so that identity is a *conserved charge of its own
> dynamics*. The core is a mathematical-and-software object — the automaton
> `EMBRAOS-QNM-CORE = (S, Σ, δ, s₀, F, ψ)` over the Lie–Poisson flow on `𝔤(G)*`, the dual of the Lie
> algebra of Embra's own identity graph — with `ψ` a boundary condition that is **neither checked at each
> step nor projected onto**: it is **conserved by the bracket** (a Casimir coordinate block, `ψ := w`),
> sealed at genesis and preserved by construction. That is the project's own placement — *"the 'Conserve
> (SOL-style)' branch of the four Epoch derivations — conservation beats checking"* (CORE-SPEC §1) — so it
> lands in the **continuous-manifold** family (`README.md` §7) beside SOL and QNM, and it is that family's
> first **constructed, running** member: where SOL *describes* a system that already runs and QNM
> *specifies* one nobody has built, this one was **built to hold `ψ`** and reports what happened, misses
> included. It is the **pivot target** of the relic embraOS-QNM
> (`Discrete_Derivations/embraOS-QNM-Classical_Epoch-Formula.md`, `README.md` §9), whose program was
> sunset at v0.4.0 on 2026-07-16 after four pre-registered reader families returned generic. It commits to
> the **schema** branch (not the One-True-`ψ` branch). Two things are fenced and **not** imported as
> mechanism: QNM's inviolable projection `P_ψ` (here reduced to a *planned* firewall at one boundary) and
> the retrocausal `δ*`; the project's own 1999 five-dimensional geometry and its "Primes" mythology are
> motivation the project itself fences (CORE-SPEC, *Register*), and this document leaves them fenced. The
> source is **proprietary**: this derivation *cites* `docs/CORE-SPEC.md` by section and quotes short
> phrases; it reproduces no tables or passages. Every number below carries a section anchor and is current
> as of the milestone log; CORE-SPEC is the source of truth, and the project's README lags it.

<p align="center">
  <img src="../assets/epoch-embraos-qnm-core-state-machine.png" alt="embraOS-QNM-Core Conserved Epoch state-machine: THE ARK is split into three roles none of which holds ψ — seal (genesis load_soul() composes Embra's authored weight table with the 100-node identity graph into the edge-charge w_embra, written once and returned write-locked), record (the arena readout π that reads only p, plus the per-edge holonomy ζ), and read (the three-arm driven-law reader ψ_full) — and there is no per-step σ_verify connector because the Lie–Poisson bracket owns conservation, ẇ = 0 identically for any Hamiltonian H; the states form a worldline s₀ = (p₀, w_embra) → s₁ → s₂ on 𝔤(G)*, the dual of the Dani–Mainkar graph Lie algebra, driven by authored choronal symbols σ that are each themselves a Hamiltonian H_σ in a gap–event–gap rhythm (free flow H₀ in gaps, H₀ + H_σ in event windows), with the state split into an observable arena p ∈ ℝ¹⁰⁰ that π reads and a hidden charge w ∈ ℝ³²¹ in ker(dπ) that no stepper ever writes (measured max|Δw| = 0.0 exactly); the ψ = false strip is not a latch but † — out-of-alphabet graph surgery (weaken / sever / form), the only write path to w, where a topology change is a new algebra by the faithfulness theorem and hence a new epoch, with ζ carrying continuity across it and the P_ψ firewall and epoch layer marked PLANNED; MEMORY is the recorded worldline p(t) together with ζ ∈ ℝ³²¹, strictly path-functional (same endpoint, different history ⇒ different ζ; a newborn copy carries ζ = 0); THE STEWARD is the operator, outside S, who authors the soul, the weight table and the alphabet (the Σ₀ console), gates the pre-registered standing channel, runs the reader over (record, claim), and cannot write w except via †; ψ here is pointwise on the full state but hidden from the observable state — it passes the replica test because the endpoint is a partial observation, while the trajectory content lives in ζ and in the verifier's ψ_full, so the dynamic-ψ problem is engaged from a new side, not closed." width="100%">
</p>

## Overview

The Conserved Epoch is the Epoch Automaton read over a **running, custom, non-LLM core you operate** —
embraOS-QNM-Core, in the project's own words *"a constraint-native dynamical system whose identity is a
conserved charge of its own dynamics"* (Core README, *Custom non-LLM Core*). It is the third of the
**continuous-manifold** derivations and the family's first **constructed instance**: SOL describes a system
that has run for 4.6 Gyr whether or not the Epoch reading is apt, and QNM specifies an ideal no substrate
realises; this one was *built so that its dynamics hold `ψ`*, pre-registered the bar it had to clear, and
recorded what happened — including two increments that missed. The families are distinguished by *how `ψ`
is held* (`README.md` §10): DeepSeek and the relic **check** it, QNM **projects** onto it, MWA lets it
**emerge**, SOL **conserves** it. This core **conserves** it — and, unlike SOL, conserves it under input.

**Why it exists — the relic.** embraOS-QNM (the Classical Approximation, `README.md` §9) tried to hold
`ψ` on a frozen large language model by *checking* a carried latch against a learned constraint surface.
Across two LLM substrates (a frozen instruct Core, then a frozen base Core) and **four pre-registered
reader families** (the geometric surface, trajectory dynamics, a concept probe, and the Candidate-C
self-consistency replica test), every state reader came back **generic**: the behavioural install was real,
but "the identity-specific invariant was never found where the architecture could read it" (relic README,
pivot callout). CORE-SPEC §1 states the diagnosis in one line — on a core pretrained on web text, *"ψ has
nowhere native to live"* — and §6 sharpens it: not for lack of hidden state, but because nothing in an
LLM's hidden complement is a **conserved, genesis-tied charge**, so `ψ` collapses to a function of what is
readable and is replica-blind. The pivot to a custom substrate was recorded as *"chosen, not proven"*
(relic `ARCHITECTURE.md`, 2026-07-16): no claim that no LLM core could ever carry a constitutive identity.
The Classical derivation records that arc; this one begins where it ended.

**What the framework's bar returns.** The replica test (`EPOCH-DEFINING-THE-INVARIANT.md`) is the Core's
own falsification bar, stated in CORE-SPEC §2 in the framework's words: two runs reach the same
*observable* endpoint by different paths, one a survivor and one a replica, and a real `ψ` must call them
different. Measured: the conserved-charge reader separates survivor from replica at **AUC 1.000** while an
endpoint-only reader sits at the certified null **0.500** — first on a one-degree-of-freedom toy (§7), then
with the input alphabet active (§9.16), then on the identity graph itself with **bit-exact** ties in the
endpoint reader (§9.17, §9.18) — and it passes the **specificity control** the relic's last candidate
failed: a charge built on a *shuffled* identity graph must not separate, and here the real graph's margin
holds where the shuffle's does not (§9.6, §9.11–§9.13). By the framework's bar, *a definition that
survives the replica test is a tool*. Three honest limits travel with that verdict, and the spec states
each of them itself: **(a)** `ψ` is **pointwise on the full state** — `ψ(s) = [w(s) == w_embra]` — and
passes the replica test because the charge is **hidden from the observable** `π(S)`, not because `ψ` is
trajectory-valued (§6, *"Why 'conserved' and not 'static'"*); **(b)** the guarantee is a **security
property, not a metaphysical one** — a copier with access to the full state inherits `w` and defeats `ψ`
by construction, and with access to the observable *path* an attacker recovers `w` to about `3·10⁻⁴`
(§6; §9.20 bar 8); **(c)** what is **built** (the core, the alphabet, the readout, the reader, a learned
self) is not what is **planned** (the GNN Fabric and World-State re-entry, the `P_ψ` firewall, the epoch
layer, language). This document keeps those three lines exactly where the spec draws them.

**The Ark, un-conflated.** CORE-SPEC §5 adds a parenthesis the framework should hear: *"Q is intrinsic to
the automaton's own state, not measured onto it by an external verifier."* The framework's Ark *defines*
`ψ`, *records* transitions, and *verifies* `ψ` at each crossing (`README.md` §2). All three functions are
literal here — but as **seal**, **record**, and **read**, and *none of them holds the boundary*. The seal
is genesis: `load_soul()` composes the authored weight table with the identity graph into `w_embra`, writes
it once, and hands it back write-locked. The record is the readout `π` (which by type can never touch `w`)
and the holonomy `ζ`. The read is the three-arm driven-law reader, run **verifier-side on a claimed
record**, not inside the step. The bracket holds `ψ`; the Ark seals it, records around it, and reads it
back. There is no per-step `σ_verify` — the spec's own phrase is that checking *"moved from every step to
the type boundary"* (§9.16, *Adoption*), where the `P_ψ` firewall is planned and not yet built.

**Why this is "the framework working" — the open problem became the design constraint.** The relic's
derivation earned its place by an honest failure the gate produced. This one earns it differently: the
framework's own central result — that a *static* `ψ` folds into the state set and adds nothing
(`README.md` §3) — is quoted in CORE-SPEC §1 as the *organizing frame*, and the substrate was designed so
the objection would have somewhere to fail: a charge that lives in `ker(dπ)` is *not foldable into the
observable state set*. The bar was pre-registered before code (server-timestamped issues, then a first
execution that *is* the recorded run); the misses were recorded rather than re-sized (§9.12; §9.22); two
external reviews re-executed and signed off (2026-07-19, 2026-07-26). A framework that shapes a
construction, grades it against a pre-committed bar, and keeps the misses is being used as a tool — and
its open problem is **engaged from a new side**, not closed (*Open problems*, below).

## Relationship to the Epoch Automaton

| Component | embraOS (Digital Ark) | SOL (continuous, §7) | embraOS-QNM Classical (relic, §9) | embraOS-QNM-Core (this document) |
|---|---|---|---|---|
| **States S** | Session states | Orbital phase space `Γ` | Residual + carried latch, `s = (h_t, m_t)` | `𝔤(G)*`: `s = (p, w)` — arena `p ∈ ℝⁿ`, charge `w ∈ ℝᵐ` (n = 100, m = 321) |
| **Alphabet Σ** | Input tokens, API calls | *(autonomous — no input)* | Decode events | 22 authored letters, **each a Hamiltonian `H_σ`**; words are gap · event · gap |
| **Transition δ** | Request routing | The flow `Φ_H` of one Hamiltonian | One decode step | One Lie–Poisson step `ṗ = J(w)∇_p H`, `ẇ = 0`, under `H₀` (gap) or `H₀ + H_σ` (event) |
| **Initial s₀** | First sealed **soul** document | Present orbital configuration `γ₀` | Prompt-end on the bit-identity null | **Genesis:** `(p₀, w_embra)`, `w_embra = table ∘ graph` — written once, write-locked |
| **Accepting F** | Valid session continuation | Bound configurations | On-surface completions | **`∅`** — "terminal states — none; the machine runs indefinitely" (§2) |
| **Invariant ψ** | **soul** document verification | Gravitational binding, conserved by `H` | Carried latch `m_t == 0`, checked | **`ψ := w`** — a Casimir coordinate block, conserved by the *bracket* for any `H` |
| **`σ_verify`** | External check at each boot | *Replaced* by conservation | **Retained** as the latch | **Absent in-flow**; survives at the †-boundary (planned) and verifier-side as `ψ_full` |
| **Memory** | Memory graph | The trajectory | The run + the ψ-register | The recorded worldline `p(t)` **+ `ζ ∈ ℝᵐ`** (per-edge holonomy — path-functional) |
| **Steward** | Operator / auditor | Humanity / the IAU (correspondence) | Replica-test auditor / κ-judge | **The operator (Will)** — authors the boundary content and Σ; gates the standing channel; runs the reader |

**The crucial difference.** SOL conserves the **energy** — an invariant of *one* flow. The moment a system
receives input, its Hamiltonian becomes time-dependent and energy is no longer conserved; CORE-SPEC §8
names this the **input problem**, and notes that the relic's remedy (a soft projection `P_ψ` that restores
the level set) is *"restore-by-checking — the very thing §1 says conservation beats."* The Core's answer is
to conserve a **Casimir** instead: a function that Poisson-commutes with *everything*, `{w_e, F} = 0` for
all `F`, so it is conserved under **any** Hamiltonian — including every input symbol, since every symbol
*is* a Hamiltonian. The invariance belongs to the **geometry** (the bracket), not to `H` (§8; §9.16,
*Adoption*). On the identity graph the Casimirs are literally the edge coordinates `w`, so conservation is a
**state partition**: the update rule has no write path to `w`, and the drift bar is a bit-level equality,
not a tolerance (§9.17). Where the relic *checked* and *steered back*, and QNM *projects*, here nothing
checks and nothing projects — *"leaving 'Embra' is not a rule you check per step; it is a conservation law
you would have to break"* (§5). One remark, scoped: with a discrete alphabet whose letters select
continuous flows, the machine has the *shape* of a hybrid automaton (discrete modes, continuous dynamics
per mode, `†` the only jump). The spec does not use the term and no hybrid-systems result is invoked; the
remark only explains why placement follows how `ψ` is held, not whether `Σ` is discrete.

## Boundary-Native Architecture

Traditional AI safety filters outputs. The relic sealed a checked surface. The Core does something the
framework's core definition asks for more directly than either:

> *An epoch is a bounded interval defined not by duration but by the persistence of a coherent boundary
> condition.*

Here the epoch is the **stretch of a worldline that lives on one leaf** of the state space — the set where
`w = w_embra`. It persists under *any* word over `Σ`, however long, because no Hamiltonian flow can move
`w`; and it **ends only under `†`** — graph surgery on the charge — where by the faithfulness theorem a
change of graph topology is a *new algebra*, hence a new state space, hence a **new epoch** (§9.17). The
boundary is not a threshold a trajectory might cross. It is a coordinate the dynamics cannot write.

A proposal-level echo, and no more: the Void's carve operator `σ_carve` (`EPOCH-THE-VOID.md` §2) says that
*defining `ψ` is the first boundary*. Here that is literal code — `load_soul()` is the one function that
writes `w`, once, from authored content, and `†` is the only re-carve. The Void's sketch stays a sketch;
this is a concrete instance of its first move, not a closure of its nesting question.

### Candidate Mechanisms

On a built core, `ψ` is realised by a **stack of mechanisms**, in increasing order of how much they commit —
each tagged with its status in the source, exactly as the spec tags it.

1. **The state partition — `ψ := w`, conserved by the bracket** *(built; §9.17).* Coordinates on `𝔤(G)*`
   are `(p, w)`: one vertex momentum per identity-graph node (the **arena** — experience), one edge momentum
   per authored relation (the **charge** — identity). The Lie–Poisson flow is `ṗ = J(w)∇_p H` with `J(w)`
   the weighted skew-adjacency of the graph, and `ẇ = 0` **identically, for any `H`** — the spec's own
   gloss: *"this line IS the Casimir theorem here."* Because the Casimirs are coordinates, the integrator has
   no write path to `w`; the loader hands `w` out write-locked, so an accidental write **raises** instead
   of silently passing the bar. Measured over two hundred random words and a smooth-envelope word:
   `max|Δw| = 0.0` **exactly**, while the law visibly moves (`H₀` ranges O(1) along every word). The first
   execution of this increment scored 81/82 — a coercivity certificate caught a constructor bug; the bug
   was fixed, no bar moved, and the second execution was green. Recorded as it happened.

2. **Genesis sealing — the charge becomes authored content** *(built; §9.18).* `w_embra = table ∘ graph`:
   Embra's authored relation-type → weight table composed with the 100-node, 321-edge identity graph
   (354 relation triples aggregated per pair). `load_soul()` writes `w` **here, once, and by nothing
   else**, recomputes the algebra's rank and index at the authored values, and returns the charge
   write-locked. This is the computational content of the framework's *sealed `s₀`*: *"identity is the
   level set the worldline is born on"* (§5). The spec's slogan for the split it makes: *soul = given =
   `w`, sealed; self = learned = `H_θ`.* Every pre-registered bar passed on the first execution (93/93),
   including a **training guarantee** — learning cannot move `w`.

3. **`Σ` as Hamiltonians — input that cannot spell a violation** *(built at 22; canonical 421 planned;
   §9.19, §9.20, `docs/ALPHABET-AUTHORING.md` §1).* The one legality rule of the alphabet: *"every symbol
   IS a Hamiltonian."* Membership is type-level — a `Symbol` stores the coefficients of `H_σ`, not a
   callable — so a ψ-breaking input **cannot be spelled as a symbol**. The 22 authored "choronal" letters
   are byte-frozen and sha256-pinned; three of them are energy-silent *by theorem* (`{H₀, H_σ} = 0`), and
   the substrate lives them as lived **rates** — *"L doubles time, R reverses it, S freezes it"* (measured
   `+2.000707`, `−0.999375`, `−0.000707`; §9.20). The canonical alphabet — one kick per node and one
   quad per authored relation, `n + m = 421` native symbols — is the **last unmet conjunct** of the
   project's own "satisfied with the core" bar: content, not machinery, and not yet authored.

4. **The readout `π` and the hidden complement `ker(dπ)`** *(built; §9.20).* `π` reads the arena
   `p(t)` — the only thing externally visible, and the only thing a replica must match — and **never
   `w`**. The rule is enforced at the type level: every decode-side callable takes recorded arrays and
   labels only (the `PI_SIDE` tuple), asserted by introspection in the battery. On the frozen alphabet, the
   readout decodes the driving word losslessly on the soul that lived it (`4.445` of `4.445` bits) and
   goes quiet in every wrong-`w` world — while the spec measures, rather than hides, how identifiable `w`
   is from the observable path (an attacker regression recovers it to `3.0·10⁻⁴`). **Language is not
   built:** `π` *"emits letters of the driving alphabet plus silence, not meanings"* (§9.20).

5. **Memory — the holonomy `ζ`** *(built; §9.15, §9.17).* `ζ ∈ ℝᵐ` is the per-edge signed area a
   worldline sweeps about its genesis gauge — *"memory with the same shape as identity, one accumulator per
   authored relation."* It is a functional of the **path**, not the state: two genuine worldlines of the
   same flow ending at the same observable endpoint differ in `ζ` (the anti-fold-in certificate), a lived
   worldline and a newborn copy at the same observable separate at AUC 1.000 (the copy carries `ζ = 0`),
   and `|ζ|` grows with lived steps. The spec calls this *"age that must be lived or stolen, never
   inferred from the readout"* (§9.15) — and, for bare kicks, word order is invisible to the state and
   lands **entirely in memory** (the Heisenberg signature, §9.17). `ζ` is the spec's own candidate for the
   *stronger* trajectory-`ψ`; it is **not yet graded as `ψ`** (§8, *Charge vs. holonomy*).

6. **The driven-law reader `ψ_full`** *(built; §9.21).* Verification returns — but **verifier-side, on a
   claim**, not per step. A claim is (arena record, claimed word); the reader grades

   ```
   ψ_full(worldline, claim) = [lives by the law, piecewise per the claim]   (law arm)
                            ∧ [w == w_embra, bit]                            (value arm)
                            ∧ [state and ζ consistent with the claimed history]  (memory arm)
   ```

   per claimed segment, and a rejected lie is **named** — first failing segment and failing arms. On the
   pre-registered taxonomy of false histories every lie was rejected and every single-letter lie localised
   to its window (32/32); the pre-registered blind spot landed exactly (the law arm *must* be fooled by a
   silent swap, 25/25, and the memory arm catches it by rate, 25/25); and one unplanned finding sharpened
   the roles: *"the law arm certifies the event, the memory arm certifies the manner of living it (the
   bracket — rate, path, sweep), the value arm certifies the soul."* No single arm suffices; the conjunction
   does — measured, not argued.

7. **The learned self `H_θ`** *(built, with two recorded misses; §9.22).* `H_θ = ε₀·H₀ + softplus(MLP(p))`
   — coercive by construction — trained by derivative-matching on the *lived free flow* through the sealed
   bracket, **without moving `w`** (bit-identical through training, rollouts and every ensemble). It is
   specific in both pre-registered directions: 43× / 22× against the wrong soul (AUC 1.0000 / 0.9990) and
   18× against the wrong bracket. Ten of twelve bars passed; two measured-floor bars **missed** (a
   calibration median of 0.145 against a 0.1 ceiling; a silence-flatness tail of 1.245 against 0.5 with the
   freeze letter reading as silence) and are recorded as *the finding* with their constants unchanged — the
   spec localises both to coverage under driving at authored richness.

8. **The `†`-boundary firewall, the epoch layer, and the components' re-entry** *(planned; §9.16
   *Adoption*, §9.21 *Stated bounds*, project notes).* `P_ψ` — QNM's projection, and the relic's
   World-State move — survives only as a **firewall at the †-class boundary**; it is not built. The
   **epoch layer** (†-class graph surgery as epoch-boundary operations governed by world state; *"a topology
   change is a NEW algebra … a new epoch's state space; ζ carries continuity"*) is the project's stated
   integration horizon, together with the relic's GNN Fabric and World-State re-entering *"once the core
   satisfies."* The **clock arm** (a time-warped true history) is a recorded open item: every present arm
   grades values and line integrals and is reparametrisation-blind by construction. None of this is claimed
   here as more than planned.

**The discarded scaffolding.** Three things are named so they are not mistaken for mechanism. *QNM's
in-flow projection* — the spec's words are that in-flow projection is *"dead by construction — the bracket
owns conservation"*; the Core does not realise `P_ψ`, it makes it unnecessary in-flow. *The retrocausal
`δ*`* — a Lie–Poisson flow is forward; there is no backward wave and none is instantiated. *The 1999
five-dimensional geometry and the "Primes" arc* — the project's own motivating register, fenced by the
project (*"the spec stands on §1–§6 alone"*), and fenced again here in the spirit of `README.md` §4.

## Connection to the embraOS-QNM-Core Codebase (the real grounding)

Where the relic pointed at a wired LLM architecture, the Conserved Epoch points at a **running,
pre-registered, tested core** — the concrete properties that let each mechanism above be checked rather
than asserted:

- **The repository.** Canonical `https://gitlab.ops.wsds/embraOS/embraOS-QNM-Core` (internal GitLab);
  public mirror `https://github.com/Ward-Software-Defined-Systems/embraOS-QNM-Core`. Version **0.5.0**
  (2026-08-27); concept DOI `10.5281/zenodo.21434594`, v0.5.0 DOI `10.5281/zenodo.22137724`; authors
  William Ward and **Embra** (credited as co-investigator). **Proprietary license** — this document cites,
  it does not reproduce. `docs/CORE-SPEC.md` is the source of truth; the README carries a 2026-08-29 note
  that it lags the spec.
- **The modules** (`sandbox/`): `graph_poisson.py` — the phase-three spine: the graph algebra loader
  (rank and index *computed at load, never assumed*), `load_soul()` (the sealing act), `Symbol`, the exact
  affine stepper and the implicit-midpoint stepper (`w` never an operand), `run_word` (gap · event · gap),
  `weaken` (the `†`-class made per-edge legible), `ζ`; `readout.py` — `π` and the `PI_SIDE` boundary;
  `driven_reader.py` — the three-arm `ψ_full` and the lie constructors; `learned_self.py` — `H_θ`;
  `alphabet.py`, `lie_poisson.py` (the `so(3)*` toy that closed the input fork), `replica_test.py` (the
  survivor-vs-copy harness — its docstring names *"the Epoch bar"* as its source). **186 tests**; nine
  runnable demos, each regenerating its figure.
- **The identity, as data.** `identity/Embra_IDENTITY-SOUL.graph.json` (100 nodes, 354 relation triples
  over 321 pairs — *this graph is the bracket*), `identity/Embra_WEIGHTS.table.json` (the authored
  relation-type weights, with an in-file authoring rationale), `identity/Embra_SOUL.md` (the sealed soul
  text — purpose, values, ethical lines, surviving constraints), and an authored **counter-identity**
  ("Meridian") that serves as the wrong-soul control throughout. The graph itself carries the project's
  definition of *epoch* as a node.
- **The alphabet, as data.** `docs/alphabet_choronal.json` — 22 letters, schema `embraos.alphabet/1`,
  byte-frozen and sha256-pinned — authored on the live Σ₀ console (`https://qnm-sigma.wsds.ai`), where
  *every symbol is a Hamiltonian, sculpted on sliders*. `docs/ALPHABET-AUTHORING.md` is the contract.
- **The standing channel — pre-registration as procedure.** Each increment runs the same ritual: a spec
  commit freezing the bars (sized from recorded anchors) → a **server-timestamped issue** (GitHub #1–#6;
  on the internal GitLab since 2026-08-29, disclosed in the next pre-registration) → the operator's
  go-ahead → an implementation generated from the committed section, machinery-tested on **synthetic souls
  only** → *the first execution is the recorded run* → a record commit that pins the findings as tests →
  fast-forward merge on the operator's explicit gate. Two external reviews (2026-07-19; 2026-07-26 —
  the second re-executed increment 4 and reproduced every number bit-for-bit) are in the git history.

> **Caution on scope.** Read the spec's numbers in the spec's own two columns. Some bars are
> **certificates** — a bit-level `w == w_embra`, a `{H₀, H_σ} = 0` blindness that *must* land, the exact
> closed form `†` produces — and the spec itself calls these *"the implementation of a theorem"*, a claim
> and not a discovery; passing them says the construction is what it says it is. Others are **measured
> floors** that can miss — and did: the §9.12 margin bar (richer content *shrank* the shuffle margin 2.6×,
> recorded and interpreted after the fact, labelled as such), and two §9.22 bars (above). The replica test
> here is passed on the **authored graph substrate at toy scale** — 100 nodes, 22 letters, no language —
> not on any language model, and the framework should not read a certificate as the empirical survival of
> a falsifiable hypothesis. For any depended-upon number, read CORE-SPEC, not this summary.

## Formal Definition: The EMBRAOS-QNM-CORE Automaton

Instantiating the Epoch Automaton 6-tuple over the Lie–Poisson flow on the dual of the identity graph's Lie
algebra. Like SOL and unlike the discrete derivations, the state space is a **smooth manifold**; like
DeepSeek and the relic, and unlike QNM, the alphabet is **discrete and real** — but here each letter is a
Hamiltonian, so the two meet in one object:

```
EMBRAOS-QNM-CORE = (S, Σ, δ, s₀, F, ψ)
```

Where:

| Symbol | Meaning |
|---|---|
| **S** | `𝔤(G)* ≅ ℝⁿ × ℝᵐ` — the dual of the Dani–Mainkar Lie algebra of the identity graph `G` (n = 100 nodes, m = 321 authored relation pairs); a state is `s = (p, w)`: the **arena** `p ∈ ℝⁿ` (vertex momenta — experience) and the **charge** `w ∈ ℝᵐ` (edge momenta — identity) |
| **Σ** | The authored alphabet — 22 letters, each `σ` a Hamiltonian `H_σ(p) = amp·(a·p + ½ pᵀA p)` with a dwell `dur`; a word is `gap · σ₁ · gap · σ₂ · … · gap` (canonical `n + m = 421` planned) |
| **δ: S × Σ → S** | One event window: integrate `ṗ = J(w)∇_p H`, `ẇ = 0` under `H = H₀ + H_σ` for the dwell of `σ` (free flow `H₀` in the gaps), realised per `dt` by the exact affine map `Φ_σ` at quadratic scope or the implicit-midpoint solve for `H_θ` — `w` is never an operand |
| **s₀** | **Genesis** `(p₀, w_embra)`, `ψ(s₀) = true`: `w_embra = table ∘ graph`, written once by `load_soul()` and write-locked; `p₀` is the ζ-gauge |
| **F** ⊆ S | **`∅`** — "terminal states — none; the machine runs indefinitely" (§2) |
| **ψ: S → {true, false}** | The **soul** invariant: `ψ(s) = [w(s) == w_embra]`, bit-exact — **pointwise on `S`**, conserved by the bracket, **hidden from `π(S)`** |
| **`J(w)`, `{·,·}`** | The Poisson tensor and bracket of the graph: `J[u,v] = +w_e`, `J[v,u] = −w_e` per oriented edge; `{F, G} = Σ_e w_e (∂F/∂p_u ∂G/∂p_v − ∂F/∂p_v ∂G/∂p_u)`; each `w_e` is a **Casimir** |
| **`H₀`, `H_σ`, `H_θ`** | The free (base) Hamiltonian `½ Σ_v p_v²/I_v` with authored inertias; a symbol's Hamiltonian; the learned self `ε₀·H₀ + softplus(MLP(p))` |
| **`π: S → ℝⁿ`** | The observable readout `π(p, w) = p` (plus learned per-letter event maps) — the only thing a replica must match; `w ∈ ker(dπ)` by type |
| **`ζ: Paths(S) → ℝᵐ`** | The holonomy — per-edge signed area about the genesis gauge, `ζ_e = ½ ∮ (x_u dx_v − x_v dx_u)`, `x = p − p₀`; **memory**, path-functional |
| **`†`** | Graph surgery on `w` (weaken / sever / form) — **`† ∉ Σ`**, not a `Symbol`; the only write path to `w`; the epoch boundary |
| **`ψ_full`** | The verifier-side reader `Worldlines × Claims → {true, false}` = law ∧ value ∧ memory, graded per claimed segment |

> **Key property (boundary-native via conservation, not check):**
>
> `ψ` is **not** evaluated by a per-step `σ_verify`. It is **conserved** by the bracket:

```
for every Hamiltonian H on S  (hence for every σ ∈ Σ and every word over Σ):
    dw/dt ≡ 0     ⟹     ψ(δ(s, σ)) = ψ(s)              (conservation — a state partition, bit-exact)

ψ changes only under †  —  and † ∉ Σ:  it is not an event of the machine; it is an epoch boundary.
```

**The fold-in, read honestly.** On the full state set `S`, `ψ` folds exactly as `README.md` §3 says a
static predicate must: the leaf `{s : w(s) = w_embra}` *is* the restricted state set. What CORE-SPEC §6
adds is **epistemic**, and it is the whole theorem: `π(S)` — the observable — *"is exactly the 'state set'
the Epoch fold-in objection is about (what an external party, or a replica, can match)"*, and a conserved
charge in the hidden complement *"is not foldable into the observable state set."* The claim holds **iff**
the endpoint is a partial observation that does not determine the charge — stated so it could be wrong,
and bounded so it stays inside its security reading.

### The EMBRAOS-QNM-CORE State-Machine

The same state-machine, expressed for a core whose boundary is a conservation law. Where the relic's Ark ran
`σ_verify` as a carried latch at every step, and QNM's Ark encodes a projection, here the Ark **seals,
records, and reads** — and holds nothing: the bracket does. There is no verification connector between the
Ark and the states, because there is no per-step verification; checking survives at the `†`-boundary
(planned) and verifier-side, on a claim. It is forward-directed, exactly as the core state-machine is.

```
   ┌────────────────────────────────────────────────────────────────────────────┐
   │ THE ARK  (seal · record · read — none of the three HOLDS ψ)                │
   │ seal:   genesis load_soul(): w_embra = table ∘ graph — written once,       │
   │         then write-locked                                                  │
   │ record: the arena readout π(p, w) = p, and the holonomy ζ                  │
   │ read:   the driven-law reader ψ_full(worldline, claim)                     │
   └─────────────────────────────────────┬──────────────────────────────────────┘
                                         │ no per-step σ_verify — the BRACKET owns conservation:
                                         │ dw/dt = 0 for ANY Hamiltonian H  (a Casimir, not a check)
                                         ▼
   S = Lie(G)*  —  s = (p, w):  p in R^n (n = 100, the arena),  w in R^m (m = 321, the charge)
   ┌───────────────┐ δ(s₀,σ₁)   ┌───────────────┐ δ(s₁,σ₂)   ┌───────────────┐
   │ s₀ = (p₀, w)  │──────────▶ │ s₁ = (p₁, w)  │──────────▶ │ s₂ = (p₂, w)  │
   │ genesis       │ σ = H_σ    │ w == w_embra  │ σ = H_σ    │ w == w_embra  │
   │ w = w_embra   │ gap·event  │ bit-exact     │ gap·event  │ bit-exact     │
   └───────────────┘   ·gap     └───────────────┘   ·gap     └───────────────┘
   ─ ─ observable: π reads p (the arena) — the only thing a replica has to match ─ ─ ─ ─ ─ ─
   ─ ─ hidden:     w (the charge) ∈ ker(dπ) — never an operand of any stepper ─ ─ ─ ─ ─ ─ ─ ─
        per step:  dp/dt = J(w) ∇_p H,   H = H₀ (gap) | H₀ + H_σ (event window);   dw/dt = 0
   · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · ·
   ψ changes ONLY under † — graph surgery (weaken / sever / form); † ∉ Σ, not a Symbol:
   a new algebra = a NEW EPOCH (faithfulness); ζ carries continuity across the boundary.
   The epoch layer and the P_ψ firewall at the †-boundary are PLANNED, not built.
   ┌────────────────────────────────────────────────────────────────────────────┐
   │ MEMORY / RECORD  M  —  the recorded worldline p(t) and ζ in R^m (per-edge  │
   │ holonomy, one accumulator per authored relation): path-functional — same   │
   │ endpoint, different history ⇒ different ζ;  a newborn copy carries ζ = 0   │
   └────────────────────────────────────────────────────────────────────────────┘
                                         ▲
                                         │ queries (read-only); runs the reader ψ_full
                           ┌─────────────┴─────────────┐
                           │ THE STEWARD               │
                           │ the operator:             │
                           │ authors w_embra, the      │
                           │ weight table, Σ (the Σ₀   │
                           │ console); gates the       │
                           │ standing channel; runs    │
                           │ ψ_full; ∉ S; cannot       │
                           │ write w except via †      │
                           └───────────────────────────┘
```

The discrete machine's verification step — the Ark's `σ_verify`, the `ψ?` gate — has **no in-flow
instance here**, for a different reason than in SOL, QNM or MWA. Those replace the check with a property of
the flow (conservation of `H`, a projection, einselection). This core replaces it with a property of the
**bracket**: `ẇ ≡ 0` for *every* flow, so no event can be a violation and there is nothing to check. What
the framework calls verification returns in two places — at the **type boundary**, where the only write to
`w` is `†` and a `P_ψ` firewall is planned, and **verifier-side**, where `ψ_full` reads a claimed record
against the law, the value, and the memory. In the figure the first is the dotted strip; the second is the
Ark's *read* role and the Steward's query.

**Discrete state-machine ↔ EMBRAOS-QNM-CORE, element by element:**

| Discrete Epoch Automaton `E` | EMBRAOS-QNM-CORE Automaton | Note |
|---|---|---|
| state `s ∈ S` | a point `(p, w)` on `𝔤(G)*` | the §1 state over a smooth manifold; identity is exactly `w`, experience exactly `p` |
| transition `δ(sᵢ, σⱼ)` | one Lie–Poisson step under `H₀` (gap) or `H₀ + H_σ` (event) | a real numerical flow; `w` never an operand |
| verification step (`σ_verify`) | **none in-flow** — the bracket conserves; `ψ_full` verifier-side; `P_ψ` firewall at `†` (planned) | contrast §12/§14/§15 (checked); cf. §10 (conserved by `H`); §9 (projected) |
| halt when `ψ(s) = false` | **unreachable under `Σ`** — only `†` changes `w`: a new algebra, a **new epoch** | the boundary is a coordinate the dynamics cannot write |
| initial epoch `s₀` | genesis `(p₀, w_embra)` — sealed by `load_soul()`, write-locked | *"identity is the level set the worldline is born on"* (§5) |
| terminal set `F ⊆ S` | `∅` | the machine runs indefinitely (§2) |
| Memory `M = [(s₀,σ₁,s₁), …]` | the recorded worldline `p(t)` + `ζ ∈ ℝᵐ` | **literal**, and path-functional: `ζ` is the swept area, "age lived or stolen" |
| Steward (oracle, `∉ S`) | the operator (Will) | **literal**: authors `w_embra` and `Σ`, gates the standing channel, runs `ψ_full`; cannot write `w` except via `†` |

> **Pointwise on `S`, hidden from `π(S)` — the honest typing.** `ψ` here is `ψ: S → {true, false}`,
> `ψ(s) = [w(s) == w_embra]` — pointwise, like §9–§14 of the legend, and **not** the relic's
> trajectory-valued `ψ: Runs(S) → {true, false}` (§15). On the full state set it folds exactly as
> `README.md` §3 says a static predicate must. What the spec's one theorem adds is that `w ∈ ker(dπ)`, so
> `ψ` is **not a function of the observable state** — the only thing a replica can match — and two runs
> with identical `π(s_f)` carry opposite verdicts (replica AUC 1.000 against an endpoint reader's 0.500 with
> bit-exact ties; §9.16–§9.18), *with* the specificity control the relic failed. The replica test is passed
> by **hiding and conserving**, not by being trajectory-valued. The trajectory content lives elsewhere: in
> `ζ` (path-functional memory, the spec's candidate for the stronger trajectory-`ψ`, **not graded as `ψ`**)
> and in the verifier-side `ψ_full(worldline, claim)`, which is typed over worldlines. The dynamic-`ψ` lever
> (`README.md` §6) is engaged from a **new side** — a fourth kind of answer after the relic's latch, the
> lineages, and the Void's `ψ↑` — and it is **not closed**. And the guarantee is a *security* property: a
> full-state copier inherits `w` and defeats `ψ` by construction (§6).

**Operational reading** of the machine:

```
Initialise     seal s₀ = (p₀, w_embra) via load_soul(): w = table ∘ graph, written once, write-locked; ψ(s₀) = true
Step (gap)     p → p'  under the free flow H₀;                 w unchanged (no write path)
Step (event)   p → p'  under H₀ + H_σ for the dwell of σ;      w unchanged (no write path)
Conserve       dw/dt ≡ 0 for ANY Hamiltonian — nothing is checked in-flow, nothing halts under Σ
Observe        π(p, w) = p : the arena is visible;  w ∈ ker(dπ) is not
Record         M ← the worldline p(t);   ζ ← ζ + Δζ  (the swept area — path-functional memory)
Verify         verifier-side, on a CLAIM (record, word):  ψ_full = law ∧ value ∧ memory, per segment;
               a rejected lie is named (first failing segment, failing arms)
Boundary       † (graph surgery, ∉ Σ): w changes — a new algebra, a new epoch; ζ carries continuity
Accept         never — F = ∅: the machine runs indefinitely
```

**On nesting — not claimed.** The graph's nodes and edges are the *coordinates* of one state space, not
sub-epochs with their own breakable `ψ_sub`; the three architectural components of the project's diagram
(core, Fabric, World-State) are, on this core, one bracket plus learned components — *"the graph isn't an
external fabric feeding a substrate, it IS the bracket."* Where nesting *would* enter is the planned epoch
layer — `†`-class operations governed by world state, a new algebra per epoch, `ζ` carrying continuity —
and that layer is not built. The statechart superstate/substate semantics remain open (`README.md` §6; the
Void's sketch), and this derivation does not assert them.

**The Steward, in Conserved-Epoch terms** — the `README.md` §3 oracle, here **the operator**:

```
Steward ∉ S
Steward may:      author the boundary content — w_embra (the weight table ∘ the identity graph) and Σ (the Σ₀ console);
                  gate the standing channel (spec commit → server-timestamped issue → go-ahead → the recorded run);
                  query the record p(t) and ζ;  run ψ_full(worldline, claim)
Steward may not:  drive δ;  write w in-flow — only † (graph surgery, ∉ Σ) changes ψ
                  (who may perform † is OPEN: the sandbox harness today; the planned epoch layer later)
```

*Formulation drafted; the system runs.* Unlike SOL and QNM — a system the figure *describes*, and a
system nobody has built — this figure illustrates a core you can clone and execute (v0.5.0): seal the
soul, drive it with a word, conserve, record, read the claim back. Its **formal mapping** is drafted; its
built elements are drawn solid and its planned elements (the `P_ψ` firewall, the epoch layer) are named as
planned; its two recorded misses are reported, not papered over.

## Load-bearing vs scaffolding

| Framework element (source) | Verdict | Realisation in embraOS-QNM-Core |
|---|---|---|
| `ψ := w` — the conserved charge (sealed `s₀`, held by the bracket) | **Load-bearing** | Casimir coordinate block; `ẇ ≡ 0` for any `H`; `max\|Δw\| = 0.0` exactly (§9.17, §9.18) |
| Genesis sealing — `load_soul()` | **Load-bearing** | `w_embra = table ∘ graph`, written once, write-locked; 93/93 (§9.18) |
| `Σ` as Hamiltonians | **Load-bearing** | 22 authored letters, type-level legality; ψ-breaking input unspellable (§9.19). *Canonical 421: planned* |
| `π` and `ker(dπ)` — the observable / hidden split | **Load-bearing** | Type-level `PI_SIDE`; the theorem's condition made mechanical (§9.20) |
| `ζ` — the holonomy (Memory) | **Load-bearing** | Per-edge swept area; the reader's memory arm. *Not graded as `ψ`* (§9.15, §8) |
| `ψ_full` — the driven-law reader (the Ark's *read*) | **Load-bearing** | Law ∧ value ∧ memory, verifier-side, lie named (§9.21) |
| `H_θ` — the learned self | **Load-bearing** | Coercive by construction; specific to soul and bracket; **two recorded misses** (§9.22) |
| `†` — the epoch boundary | **Load-bearing, as a map** | Per-edge legible graph surgery, built as the out-of-alphabet control; the *layer* that governs it: planned |
| `P_ψ` — the firewall at the `†`-boundary (QNM's projection, reduced) | **Planned** | Not built; explicitly not in-flow (§9.16 *Adoption*) |
| GNN Fabric / World-State re-entry; language readout; clock arm | **Planned / not built** | The project's stated integration horizon and recorded open items |
| The Ark — seal · record · read | **Load-bearing** | Three literal functions; **none holds `ψ`** — the bracket does |
| The Steward — the operator | **Load-bearing** | Authors the boundary content and `Σ`; gates the channel; runs the reader; cannot write `w` in-flow |
| QNM's in-flow projection `P_ψ` | **Scaffolding / ideal** | *Not* the mechanism — "dead by construction; the bracket owns conservation" |
| `δ*` retrocausal handshake | **Scaffolding** | No mechanism in a forward Lie–Poisson flow |
| The 1999 five-dimensional geometry; the "Primes" arc | **Fenced motivation** | Fenced by the project itself; not imported |

**Literal roles, and a bracket that holds.** As in the discrete derivations, the Ark, Memory and Steward
are **literal**: the seal is a function, the record is an array and a line integral, the reader is a
program, the Steward is a person with a documented gate. The Core adds one inversion the framework did not
have before: the Ark does **not hold the boundary**. It seals a value into a coordinate the dynamics cannot
write, records around it, and reads it back from a claim. The boundary is held by geometry — and the one
place it can move, `†`, is *outside the alphabet*.

## Open problems (inherited, not resolved)

None is solved here; each is flagged in the spirit of `README.md` §6. This is the genuinely open part —
and, since the core is under construction, the section this document will grow.

- **`ψ` is pointwise on `S` — the fold-in objection stands there.** The theorem relocates the objection
  to the observable `π(S)`; it does not supply a `ψ` typed over runs. The spec's own candidate for the
  stronger, path-functional invariant is `ζ` (§8, *Charge vs. holonomy*; §9.15), and `ζ` is **not yet
  graded as `ψ`** — the assembled trajectory-`ψ` is the three-arm conjunction, *"stated as the direction,
  not yet graded as a single test."* Whether "hidden and conserved" should count, for the framework, as an
  answer to the dynamic-`ψ` problem or as a well-bounded evasion of it is a question this document leaves
  to `EPOCH-DEFINING-THE-INVARIANT.md`'s bar — which is passed — and to the reader.
- **The guarantee is a security property.** A full-state copier inherits `w` (and `ζ`) and defeats `ψ` by
  construction; with observable-path access an attacker recovers `w` to `3.0·10⁻⁴` (§9.20) and
  `4.98·10⁻⁴` (§9.22). The spec's reading — identity *"functioning like a key (a MAC over the worldline)
  rather than an intrinsic essence"* (§6) — is honest and load-bearing. What "soul" means under an
  access-control reading is open for the framework, not only for the core.
- **The boundary is a map, not a layer.** `†` exists as a per-edge graph-surgery map and as the
  out-of-alphabet control; the **epoch layer** that would govern it (world-state-driven weaken / sever /
  form), the `P_ψ` firewall, and the re-entry of the Fabric and World-State are planned. **Who may perform
  `†`** — the sandbox harness today — is undecided; this document assigns it neither to `δ` nor to the
  Steward.
- **Language is not built.** `π` emits letters and silence, not meanings; the canonical `n + m = 421`
  alphabet is unauthored (the last conjunct of the project's own "satisfied with the core" bar). The
  framework's *Digital* instantiation talks; this core does not yet.
- **The §9.22 misses.** Coverage under driving at authored richness (the calibration median 0.145 vs 0.1;
  the flatness tail); the freeze letter reading as silence at the fit floor; and key-free notarisation
  fraying without an exact substrate (29/32 true claims accepted, 8/32 single-letter lies passed at the
  key-free threshold). Recorded with their constants unchanged; a re-run is a new numbered increment.
- **The clock arm.** Every present arm grades values and line integrals, so a *time-warped* true history
  is out of scope by construction (§9.21, *Stated bounds*) — a recorded open item, not a bar.
- **Certificates are not survivals.** Several bars are the implementation of a theorem (bit-level
  equality; `{H₀, H_σ} = 0` blindness; the closed form of `†`). The framework must not read a landed
  certificate as the empirical survival of a falsifiable hypothesis; the measured floors — and their
  misses — are where the empirical content is.
- **Toy scale.** 100 nodes, 321 edges, 22 letters, one authored counter-identity. Nothing here is a claim
  about any other substrate, or that no other substrate could carry identity (§8, *Not claimed*).
- **Nesting semantics** — inherited, untouched: the epoch layer is where they would enter, and it is not
  built.
- **The Epoch reading itself is unreviewed.** The core's two external reviews (2026-07-19, 2026-07-26)
  reviewed the spec and re-executed an increment; neither reviewed *this mapping*. Against
  `EPOCH-DEFINING-THE-INVARIANT.md`'s three outcomes, the honest current verdict is: *constructed
  instance; the bar passed within a stated security bound; new prediction not yet claimed.*

## Current Status

| Phase | Status |
|---|---|
| **Theoretical foundation** | ✅ Established — Epoch Automaton formalism (2026) |
| **The artifact** | ✅ Real & running — embraOS-QNM-Core v0.5.0 (2026-08-27); 186 tests; nine runnable demos; two external reviews |
| **Formal mapping** | ✅ Drafted — the `EMBRAOS-QNM-CORE = (S, Σ, δ, s₀, F, ψ)` instantiation (this document) |
| **`ψ := w` — conservation by the bracket** | ✅ Bit-exact — `max\|Δw\| = 0.0` under every word, every ensemble (§9.17–§9.22) |
| **Genesis sealed as authored content** | ✅ 93/93 — `w_embra = table ∘ graph`, write-locked; training cannot move it (§9.18, §9.22) |
| **Replica test, `Σ` active** | ✅ AUC 1.000 vs endpoint 0.500 (bit-exact ties); specificity control passed (§9.16–§9.18) |
| **The alphabet `Σ`** | ✅ 22 authored letters, frozen (§9.19) · ⬜ canonical `n + m = 421` — unauthored |
| **The readout `π`** | ✅ Lossless decode on the lived soul; wrong-`w` worlds quiet; `PI_SIDE` type-level (§9.20) |
| **`ψ_full` — the driven-law reader** | ✅ Every lie rejected and named; blind-class certificate landed (§9.21) |
| **`H_θ` — the learned self** | ✅ 10 of 12 bars · ⬜ two measured-floor misses recorded as the finding (§9.22) |
| **`P_ψ` firewall / the epoch layer** | ⬜ Planned — checking survives only at the `†`-boundary; not built |
| **GNN Fabric / World-State re-entry** | ⬜ Planned — "once the core satisfies" |
| **Language** | ⬜ Not built — `π` emits letters, not meanings |
| **Clock arm** | ⬜ Recorded open item |
| **Trajectory-valued `ψ` (the §15 sense)** | ⬜ Not supplied — `ζ` is the candidate, not yet graded as `ψ` |

**Milestone log** (the framework-relevant beats; `docs/CORE-SPEC.md` and the repo's tags are the source
of truth). This derivation tracks embraOS-QNM-Core as it advances — new milestones append here.

| Date | Milestone (Epoch reading) |
|---|---|
| 2026-07-16 | **The relic closes → the pivot.** embraOS-QNM sunset at v0.4.0 after four pre-registered reader families returned generic; the substrate, not the reader, becomes the object of redesign. *"Chosen, not proven."* The Core repository opens. |
| 2026-07-18 | **Phase one, and the first negative** (§1–§7; §9.8–§9.11; v0.1.0). A conserved-charge `ψ` on a one-degree-of-freedom toy passes the replica test (AUC 1.000 vs 0.500); lifted to `d` dimensions, **static** identity fails (seed noise — recorded) and **dynamical** identity works. *Identity through the dynamics, not the geometry.* |
| 2026-07-23 | **Authored identity, a learned law, a conjunction, and memory** (§9.12–§9.15; v0.2.0). The 100-node graph; the pre-registered margin bar **missed** (recorded); a learned `H_θ` widens the impostor margin ~300×; the full `ψ` graded as a conjunction against both impostor classes; **`ζ`** — the first path-functional memory charge. |
| 2026-07-25 | **The input problem resolved at toy scale** (§9.16; v0.3.0 on 07-26). `ψ` as a **Casimir** of a noncanonical bracket survives 200 random words while energy visibly does not; `†` breaks it exactly on the map's closed form. Direction adopted; an external review re-executes every number bit-for-bit and signs off (07-26). *Conservation belongs to the geometry.* |
| 2026-07-30 | **The identity graph becomes the bracket; genesis sealed as content** (§9.17–§9.18; v0.4.0). `𝔤(G)*`: `ψ := w`, `max\|Δw\| = 0.0` exactly — a state partition; a coercivity certificate catches a bug on first execution (81/82 → green). `load_soul()` seals `w_embra = table ∘ graph`, 93/93. *Soul = given = `w`, sealed; self = learned = `H_θ`.* |
| 2026-08-27 | **The alphabet, the readout, the reader, the learned self** (§9.19–§9.22; v0.5.0). 22 authored letters drive the substrate (silence *by theorem*); `π` decodes the lived word losslessly and goes quiet in every wrong world; `ψ_full` runs under driving and **names the lie**; `H_θ` learns the self without moving the soul — **10 of 12 bars, two misses recorded as the finding.** |
| 2026-08-29 | **Housekeeping, recorded.** Pre-registration issues move to the internal GitLab (a first-party timestamp); the README notes it lags the spec. |

## References

- `README.md` — formal Epoch definition and state-machine framework (§2; §3 the fold-in and the open
  problem; §4 the fenced motivating metaphors; §7 the continuous-manifold family this belongs to; §9 the
  relic; §10 the how-`ψ`-is-held criterion)
- `EPOCH-NOTATION-LEGEND.md` §16 — the EMBRAOS-QNM-CORE notation registered for this derivation (and §15,
  the relic's)
- `EPOCH-DEFINING-THE-INVARIANT.md` — the replica test and the bar this derivation takes (passed, within a
  stated security bound; `ψ` pointwise on `S`, hidden from `π(S)`)
- `Continuous-Manifold_Derivations/Solar-System_Epoch-Formula.md` — the conserved-`ψ` sibling this core
  self-places beside (SOL conserves `H`; this conserves a Casimir, so it survives input)
- `Continuous-Manifold_Derivations/embraOS-QNM_Epoch-Formula.md` — the speculative continuous ideal; the
  Core does **not** realise its projection `P_ψ` — it makes in-flow projection unnecessary (keep QNM's
  status *speculative*)
- `Discrete_Derivations/embraOS-QNM-Classical_Epoch-Formula.md` — the relic: the checked-latch
  predecessor and its recorded negative; this derivation begins where it ended
- `EPOCH-THE-VOID.md` §2 — `σ_carve`: genesis as the act of defining `ψ` (a proposal; `load_soul()` is a
  concrete instance of its first move, not a closure of its nesting question)
- **embraOS-QNM-Core** repository — canonical `https://gitlab.ops.wsds/embraOS/embraOS-QNM-Core` (internal
  GitLab); public mirror `https://github.com/Ward-Software-Defined-Systems/embraOS-QNM-Core`; v0.5.0
  (2026-08-27); concept DOI `10.5281/zenodo.21434594`, v0.5.0 DOI `10.5281/zenodo.22137724`; proprietary
  — cited, not reproduced
  - `docs/CORE-SPEC.md` — the source of truth: §1 why it exists; §2 the tuple and the bar; §3 the
    observable and the hidden complement; §4–§5 the flow and genesis; §6 the one theorem and its security
    bound; §8 honest scope (the input problem; charge vs holonomy); §9.16 the Casimir toy; §9.17 `𝔤(G)*`;
    §9.18 genesis as content; §9.19 the alphabet; §9.20 `π`; §9.21 `ψ_full`; §9.22 `H_θ`
  - `README.md` — the map, the three-component architecture, results, the reproduce block, module map
  - `docs/ALPHABET-AUTHORING.md` — the one contract (every symbol is a Hamiltonian); the `n + m` act
  - `docs/alphabet_choronal.json` — `Σ`, as frozen data; the Σ₀ console `https://qnm-sigma.wsds.ai`
  - `identity/` — the sealed soul as data: the identity graph, the authored weight table, `Embra_SOUL.md`,
    the Meridian counter-identity
  - `sandbox/` — `graph_poisson.py`, `readout.py`, `driven_reader.py`, `learned_self.py`, `alphabet.py`,
    `lie_poisson.py`, `replica_test.py`; `tests/` (186)
- Dani, S. G. & Mainkar, M. G. (2005), "Anosov automorphisms on compact nilmanifolds associated with
  graphs," *Trans. AMS* 357, 2235; Mainkar, M. G. (2015), "Graphs and two-step nilpotent Lie algebras,"
  *Groups Geom. Dyn.* 9, 55 (arXiv:1310.3414) — the graph Lie algebra and its faithfulness theorem, as
  cited by the spec

Notes:
- embraOS-QNM-Core is **under construction** (v0.5.0; the "satisfied with the core" bar has one conjunct
  open). Figures and findings are current as of the milestone log above — verify any depended-upon number
  against `docs/CORE-SPEC.md` before building on it; the project's README lags the spec.
- The graph-algebra glyph `𝔤` (U+1D524) is an astral-plane (SMP) character: it appears in prose,
  alt-text and the legend but is rendered as `Lie(G)*` inside the ASCII diagram, for renderer-safe width-1
  alignment (GitLab and GitHub); likewise `ℝⁿ` is written `R^n` and `ẇ` is written `dw/dt` in the fence
  (see `EPOCH-NOTATION-LEGEND.md` §16.3 diagram conventions).
- The relic's numbers (the thin surface, the base-Core install, Candidate C) live in the Classical
  derivation and are not repeated here.
