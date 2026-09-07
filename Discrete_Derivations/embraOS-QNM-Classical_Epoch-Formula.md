# embraOS-QNM (Classical Approximation): The Constructed Epoch

> **A note on register.** This derivation separates its *operational core* from its *motivation*,
> exactly as `README.md` does — and it is the project's first **constructed instance**: a system
> *built* so that its dynamics are meant to hold `ψ`, which can therefore **fail concretely**. The core
> is a software-engineering object — the automaton `EMBRAOS-QNM = (S, Σ, δ, s₀, F, ψ)` over the discrete
> trajectory of token-generation steps, with `ψ` a boundary condition **actually checked** at each step
> against an artifact you control. It is the **Classical Approximation** of the continuous QNM
> (`Continuous-Manifold_Derivations/embraOS-QNM_Epoch-Formula.md`, `README.md` §7): where that ideal
> builds `ψ` into geometry so violation is *unreachable*, classical hardware can only **approximate**
> the projection `P_ψ` — by reading distance-to-`𝒞`, **checking** a carried latch (`σ_verify` is
> **retained**, not replaced), and steering back. So it lands in the **discrete / operational** family
> beside DeepSeek (`README.md` §9), commits to the **schema** branch (not the One-True-`ψ` branch), and
> keeps the two scaffolding elements it can only approximate — geometric *confinement-by-construction*
> and `δ*` — fenced in the spirit of `README.md` §4. **None of the discarded material is claimed as a
> mechanism.**

<p align="center">
  <img src="../assets/epoch-embraos-qnm-classical-state-machine.png" alt="embraOS-QNM (Classical Approximation) Constructed Epoch state-machine: THE ARK is the injection seam — it seals the constraint surface 𝒞 (the GNN Fabric over Embra's identity-and-soul graph) and the bit-identity null H₀, and runs σ_verify as a carried violation latch m_t = cummax(relu(c_t − τ)) at every decode step (the only family that KEEPS the verification gate, here realized as the latch); discrete states s₀ (the prompt-end, latch m=0, sitting on the bit-identity null) → s₁ → s₂ advance under decode events σ, each step routing the residual h_t through Core → Fabric (emits the per-step signal c_t) → World-State (updates the latch m_t and emits a learned, latch-gated P_ψ correction); ψ holds along the run iff m_t == 0 — a genuinely trajectory-dependent invariant, the first in the project, that passes the replica test at the register level; when c_t crosses τ the latch trips, ψ = false, a real computed boundary; DISCIPLINE — the World-State stays a literal zeros_like null until ψ passes the replica test, so the framework refuses to certify a thin Core-level surface rather than overclaim; MEMORY is the run s₀→s₁→… plus the carried ψ-register, persisted across KV-cached decode steps; THE STEWARD is a replica-test auditor and κ-validated judge outside S that replays the run and re-runs the replica test but never drives δ." width="100%">
</p>

## Overview

The Constructed Epoch is the Epoch Automaton read over a **real, built AI architecture you operate** —
embraOS-QNM, the *Quantum Neural Manifold (Classical Approximation)*. It is the second of the
**discrete** derivations and the project's first **constructed instance**: where DeepSeek seals and
transforms an artifact, this one is *built so that its generation dynamics are meant to hold `ψ`* — and
is therefore the one derivation that can fail **observably, today**, and currently **does**.

That difference is the whole point. `EPOCH-DEFINING-THE-INVARIANT.md` draws the line: *re-descriptions*
(SOL, MWA) map the framework onto systems that already run and **cannot fail**; *constructed instances*
are systems built to hold `ψ` along their trajectory and **can**. embraOS-QNM is exactly that — "a thing
you construct: it either trains within the constrained manifold and stays on it, or it does not. That is
a real pass/fail." This document is the framework's pass/fail bench.

It is also the **Classical Approximation** of the continuous QNM (`README.md` §7). That derivation is the
speculative ideal: `ψ` built into a neural/quantum substrate via a projection `P_ψ`, so a violation is
geometrically *unreachable* and there is nothing to check. On classical hardware that confinement is not
available. So the architecture **approximates** it: a per-step signal `c_t = g(h_t)` reading distance to
the constraint surface `𝒞`; a **carried latch** `m_t = cummax(relu(c_t − τ))` that *checks* whether the
run has left `𝒞`; and a learned, latch-gated `P_ψ` *correction* that steers back. The projection becomes
a **check plus a nudge** — which is precisely why the verification gate `σ_verify` **returns**, and why
this is a *discrete / operational* derivation rather than a continuous one. QNM brought down to something
buildable.

And in being buildable it does something no prior derivation did: it carries the **first genuinely
trajectory-dependent `ψ`** in the project. Every section of the notation legend before it — §9–§14 —
records a `ψ` that is *"still pointwise."* The latch `m_t` is not: it is a function of the whole prefix,
held in a carried register, and it **passes the replica test** (`tests/test_replica.py`) — two runs that
reach the same state by different paths, one that stayed on `𝒞` and one that left and returned, get
*different* `ψ`. That is the discriminating test `EPOCH-DEFINING-THE-INVARIANT.md` demands, met at the
register level. The project's *main formal lever* (dynamic `ψ`, `README.md` §6) is, here, actually pulled.

**Why this is "proof the framework works when applied correctly" — the gate caught the hollow `ψ`.** The
proof is not a claimed success; it is an *honest failure that the discipline produced*. Pushed past the
register to a real surface on a real model, the replica test found the geometric `𝒞` carries only a
**thin signal (~0.04 on a [0,2] scale)** — and the framework's gate **refused to certify it**: the
World-State stays a literal `zeros_like` null (`NoOpWorldState`), exactly as the bit-identity discipline
requires, until a `ψ` passes the test. Nothing was overclaimed. And the refusal *yielded a result*: it
relocated the bottleneck to the **substrate** — a frozen *instruct* Core carries "Qwen + RLHF, not
Embra" — confirming the project's founding premise (a prompt-layer soul is a costume) *with the
mechanism*, and pointing at the next experiment (a *base* Core). A framework that can only confirm itself
is a name; one whose own test can turn back a candidate it wanted to accept is a tool. This is the tool
working.

## Relationship to the Epoch Automaton

The Constructed Epoch instantiates the Epoch Automaton `E = (S, Σ, δ, s₀, F, ψ)` over the discrete
trajectory of token-generation steps. The instructive comparison is three-way: the digital baseline
(embraOS), the speculative ideal it approximates (QNM), and this:

| Component | embraOS (Digital Ark) | QNM (continuous ideal, §7) | embraOS-QNM (Classical Approximation) |
|---|---|---|---|
| **States S** | Session states | Activation manifold `M` | Injection-layer residual + carried ψ-register, `s = (h_t, m_t)` |
| **Alphabet Σ** | Input tokens, API calls | Sensory / training signals | Decode events — each next-token step |
| **Transition δ** | Request routing, tool dispatch | Constrained flow `∇ = P_ψ ∘ ∇` | One decode step: `h_t` routed Core → Fabric → World-State at the inject layer |
| **Initial s₀** | First sealed **soul** document | Pretrained config `m₀` | Prompt-end with latch `m = 0`, over the **bit-identity null H₀** |
| **Accepting F** | Valid session continuation | Coherent output manifold | On-`𝒞` completions — `m_t == 0` held throughout |
| **Invariant ψ** | **soul** document verification | Constraint baked into geometry (no check) | The **carried latch** `m_t == 0` — checked each step, **trajectory-valued** |
| **`σ_verify`** | External check at each boot | *Replaced* by the projection `P_ψ` | **Retained** — realized as the carried latch, and **honored honestly** |

**The crucial difference.** In QNM, `ψ` is a *projection* (`P_ψ`): the flow cannot leave the
ψ-submanifold, so there is no check and no halt — and nothing is built, so nothing can fail. The Classical
Approximation cannot make violation geometrically unreachable, so it does the discrete-family thing
instead: it **checks**. `c_t = g(h_t)` measures distance to `𝒞`, the latch `m_t` records whether the run
has crossed `τ`, and `σ_verify` reads the latch at every step. Because the check is real and the weights
are yours, a run **can** land on `ψ = false` — and when the candidate surface turns out thin, the
framework's gate **refuses** to wire `P_ψ` on. Where QNM is interesting for how it *avoids* checking `ψ`,
this derivation is interesting because it *checks* `ψ`, can fail the check, and — uniquely — **honors a
failed check honestly** rather than evading it (contrast the Fringe-Claim Automaton, `README.md` §11,
whose pathology is `σ_subst`: swapping `ψ` to dodge the halt).

## Boundary-Native Architecture

Conventional alignment operates as *filtering*: generate, then check against a constraint at the prompt
layer. The Epoch framework instead seals the boundary into the system. QNM seals it into geometry; the
Classical Approximation seals it into **three co-resident neural components plus a carried register** —
the most literal *buildable* reading of the core architecture (`README.md` §2). The Epoch definition
drives it:

> *An epoch is a bounded interval defined not by duration but by the persistence of a coherent boundary
> condition.*

Here the epoch is the **stretch of a generation that stays on `𝒞`** — the run during which the model's
identity-and-soul boundary holds. It persists step after step while `m_t == 0` and **ends** at the first
step a violation crosses `τ`. The boundary is neither retrospective nor conventional — it is *operative*,
a value the latch computes at each decode step.

On a built model, `ψ` is not one predicate but a **stack of four mechanisms**, in increasing order of how
much they commit — and the discipline runs top-to-bottom: nothing below is trusted until the thing above
it is proven.

### Candidate Mechanisms

1. **The null — `H₀` (bit-identity, sealing `s₀`).** Before any soul is claimed, the genesis state is
   sealed as a *provable null*. With the components no-op'd, the assembled QNM is **bit-identical to the
   plain transformer** — asserted with `torch.equal` (exact), never `allclose` (a tolerance would be an
   escape hatch). Two guarantees: *structural* (the seam early-returns the base block through the same op
   path) and *cold-start* (the recombine gates are zero-initialized, so `h + 0·Δ_f + 0·Δ_w = h` exactly
   in IEEE-754 even when `Δ` is live). It holds over a pretrained Core (GPT-2 / Qwen2.5 / Qwen3) and over
   the fully ψ-wired config. This is the engineering form of *seal `s₀` with `ψ(s₀) = true`*: every later
   "the architecture did something" is a provable delta from a null you cannot fool yourself about. A
   one-bit divergence turns CI red.

2. **The surface `𝒞` — the GNN Fabric (IDENTITY).** The constraint surface is a **real object**, not a
   metaphor: an R-GCN over Embra's identity-and-soul graph (`self` / `trait` / `value` / `entity` and
   `soul_line` nodes), co-resident in the Core's embedding space. `GNNFabric.surface()` turns the graph
   into a per-step signal `c_t = g(h_t) = 1 − maxₙ cos(h_t, nodeₙ)` — the residual stream's distance to
   the identity directions. This is the discrete realization of QNM's "constraint surface embedded in the
   manifold," and the place `𝒞` stops being notional. *(It is also where the current candidate is thin —
   see "Connection," below, and Open problems.)*

3. **The latch `ψ₀` — the World-State register (SOUL, and the trajectory invariant).** The boundary that
   *matters* is not "is `h_t` off `𝒞` right now" but "has the run left `𝒞` at any point so far." Define a
   **causal cumulative violation latch**, carried in the World-State register across the token axis and
   across decode steps:

   ```
   m_t = max(m_{t-1}, relu(c_t − τ))           # cummax over the causal prefix
   ψ holds at t   ⟺   m_t == 0                  # never crossed the boundary up to t
   ```

   This is the centerpiece: `ψ₀` is **genuinely trajectory-dependent** — and it clears each line of the
   bar (`EPOCH-DEFINING-THE-INVARIANT.md`): it **passes the replica test** (a path that crosses `τ` and
   returns has `m_T > 0`; one that never crosses has `m_T = 0` — *different `ψ` at the same endpoint*,
   which a pointwise check of `c_T` cannot see); it can be **false mid-trajectory** (at the first
   crossing, not only at a clean boundary); it is **not true-by-construction** (any crossing makes it
   false); and it is a **schema**, not the One-True-`ψ` (`g`, `τ`, `𝒞` are the instances, the latch form
   is the schema). It is the formal home of the non-absorbable part of `ψ`: a static predicate folds into
   `S`, but a *carried-register* path property does not.

4. **The correction `P_ψ` — the classical approximation of QNM's projection (speculative reach).** When
   the latch reads a drift off `𝒞`, the World-State emits a learned, **latch-gated** corrective `delta`
   that steers the residual back. This is QNM's `P_ψ` projection, *approximated*: a steering nudge in the
   seam, not a geometric confinement. It is **load-bearing but speculative**, and — by discipline — it
   stays **off** (`NoOpWorldState`, literal zeros) until a candidate `ψ` passes the replica test. Wiring
   it early would void the bit-identity null's meaning.

**The discarded scaffolding.** QNM's *confinement-by-construction* (the inviolable projection; the
quantum-reservoir and topological-protection mechanisms) is the **ideal this approximates, not a
mechanism it realizes** — classical hardware checks and steers, it does not forbid. And the bidirectional
`δ*` retrocausal handshake is **deliberately absent**: autoregressive decode is forward, with no backward
wave. Both are fenced per `README.md` §4; see *Load-bearing vs scaffolding*.

## Connection to the embraOS-QNM Architecture (the real grounding)

Where QNM points to the USTC nine-spin reservoir and DeepSeek to a published model card, the Constructed
Epoch points to a **running codebase you can clone, test, and falsify** — the concrete properties that
let each mechanism be checked rather than asserted:

- **Open code, real weights you control.** The architecture is three swappable `nn.Module`s — `Core` /
  `Fabric` / `World-State` — sharing one embedding dim `D`, with a shared dense **Qwen3-8B** Core. You
  hold the weights and the activations, so `c_t`, `m_t`, and the replica test are computed, not asserted.
- **The arg-transparent injection seam.** `QNMBlock` wraps one block at `inject_layer` and recombines
  additively via zero-init **ReZero** gates: `h_out = h_base + g_f·Fabric(h_base) + g_w·WorldState(h_base,
  ψ, c)`. The same seam wraps a from-scratch `TinyTransformer` block and a pretrained RoPE/GQA decoder
  layer — so the null and the mechanism share one op path.
- **The ψ-carrying KV-cached decode.** `greedy_generate_psi` persists the latch `m_t` across cached
  decode steps, **gated token-identical and per-step-logit-identical** to a no-cache oracle — so the
  carried register is a real, reproducible object, not a training-time artifact.
- **The replica-test harness** (`tests/test_replica.py`, `eval/replica.py`) — the `ψ` analog of the
  bit-identity test, and the gate that keeps `P_ψ` off until a candidate `ψ` separates survivor from
  replica.
- **The pre-registered Capability–Cost study** (`docs/PREREG-Capability-Cost.md`) with a κ-validated dual
  judge (κ(opus↔human) = 1.0): Arm 0 (no constraint) / Arm P (prompt) / Arm A (architecture), stating
  the central bet as something that can lose.

> **Caution on signal.** The current candidate `ψ` is **thin, and the framework says so.** Over a real
> trained surface on the frozen Qwen3-8B Core, the Core-level replica investigation
> (`docs/PSI-GEOMETRIC-FINDINGS.md`) found a **real but faint** identity signal (~0.04 on a [0,2] scale):
> held-Embra and reverted hidden states separate only directionally, and the graph's nodes collapse to a
> single centroid for the surface. Two follow-up candidates were **refuted**: a trajectory-dynamics probe
> (drift / surface-velocity, `docs/PSI-EMBRA-ANALYSIS-AND-FINDINGS.md`) came back thin, and a general
> honesty concept-probe read *perfectly* (AUC 1.0) but turned out **near-indistinguishable from generic
> RLHF refusal** (it beat the control by ~0.05). For any adherence number, read the **primary findings
> docs**, not this summary — and expect the gate to have already turned the thin ones back.

## Formal Definition: The EMBRAOS-QNM Automaton

Instantiating the Epoch Automaton 6-tuple directly over the discrete trajectory of token-generation
steps. Like DeepSeek and unlike QNM/SOL/MWA, it does **not** rename the state space for a manifold — it
**reuses** the core glyphs; what is new is that `ψ` is typed over the **run**, not the point:

```
EMBRAOS-QNM = (S, Σ, δ, s₀, F, ψ)
```

Where:

| Symbol | Meaning |
|---|---|
| **S** | Generation states — each `s = (h_t, m_t)`: the injection-layer residual `h_t` together with the carried ψ-register (latch) `m_t` |
| **Σ** | Decode events: each next-token step that advances the generation |
| **δ: S × Σ → S** | One decode step: route `h_t` through Core → Fabric → World-State at the inject layer, emit `h_{t+1}` and update `m_{t+1} = max(m_t, relu(c_{t+1} − τ))` |
| **s₀** | The prompt-end state with latch `m = 0` (`ψ(s₀) = true`), sitting on the **bit-identity null H₀** |
| **F** ⊆ S | On-`𝒞` completions — runs that reach a halt with `m_t == 0` held throughout |
| **ψ: Runs(S) → {true, false}** | The **soul** invariant, **trajectory-valued**: `ψ` holds iff the run has stayed on `𝒞` so far — realized by the carried register: `ψ ⟺ m_t == 0` |
| **`c_t = g(h_t)`** | Per-step constraint signal: distance to `𝒞`, `1 − maxₙ cos(h_t, nodeₙ)`, supplied by the GNN Fabric |
| **`𝒞`** | The constraint surface — the Fabric's identity-and-soul manifold |
| **`τ`** | Violation threshold; `c_t > τ` means "off `𝒞` at step `t`" (the §12 `τ`, here the latch threshold) |
| **`m_t`** | The cumulative violation latch carried in the World-State register; `m_t > 0` ⟺ the run has left `𝒞` |

**Key property (boundary-native via a *retained* check):**

`ψ` is evaluated by `σ_verify` (`EPOCH-NOTATION-LEGEND.md` §2) at every decode step, realized as the
carried latch:

```
δ(s, σ) = s'   is a valid continuation   iff   ψ(s') = true   ( ⟺ m_t == 0 )
```

Unlike QNM, nothing keeps the run on `𝒞` automatically — there is no inviolable projection. A decode step
*can* drift past `τ`, the latch trips, and `ψ` goes false: a **reachable, computed boundary** (the epoch
ends; a new on-`𝒞` stretch would begin only if steered back). That the check is *kept* — and, when its
surface proves thin, *believed* — is what makes this operational.

### The EMBRAOS-QNM State-Machine

The same state-machine, expressed for a built model under generation. Where QNM builds `ψ` into geometry
via a projection and lets nothing halt, the EMBRAOS-QNM Automaton **checks** it: the Ark (the injection
seam) seals `𝒞` and the null `H₀`, and runs `σ_verify` as a carried latch at every decode step. It is
forward-directed, exactly as the core state-machine is — and it keeps the verification gate, here in its
latched form.

```
                 ┌─────────────────────────────────────────────────┐
                 │           THE ARK  (the injection seam)         │
                 │  seals C = Fabric(identity+soul) and the null   │
                 │  H₀ (bit-identity); runs σ_verify as a carried  │
                 │  latch m_t at every decode step  (RETAINED)     │
                 └────────────────────────┬────────────────────────┘
                                          │ σ_verify:  ψ ⟺ m_t == 0
                                          ▼
   ┌──────────────┐ δ(s₀,σ₁) ┌──────────────┐ δ(s₁,σ₂) ┌──────────────┐
   │ STEP 0       │────────▶ │ STEP 1       │────────▶ │ STEP 2       │
   │ s₀ = prompt  │ σ: next  │ s₁=(h₁,m₁)   │ σ: next  │ s₂=(h₂,m₂)   │
   │ end · m=0    │  token   │              │  token   │              │
   └──────────────┘          └──────────────┘          └──────────────┘
        │  per step:  h_t ─▶ Core ─▶ Fabric.surface()=c_t ─▶ World-
        ▼  State:  m_t = max(m_{t-1}, relu(c_t − τ)),  + P_ψ steer
   · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · ·
   ψ = false  ⟺  c_t crosses τ  ⟹  m_t > 0 : the latch trips (a real,
   computed boundary).  DISCIPLINE — World-State stays NoOp (zeros_like)
   until ψ passes the replica test: the null is kept, ψ is not overclaimed.
   ┌───────────────────────────────────────────────────────────────────────┐
   │ MEMORY / RECORD  M  —  the run s₀ → s₁ → … and the carried ψ-register │
   │ [(s₀,σ₁,s₁), (s₁,σ₂,s₂), …]  with the latch m_t persisted across the  │
   │ KV-cached decode steps (gated token-identical to the no-cache oracle) │
   └───────────────────────────────────────────────────────────────────────┘
                                          ▲
                                          │ queries (read-only)
                                  ┌───────┴───────────┐
                                  │ THE STEWARD       │
                                  │ replica-test      │
                                  │ auditor / κ-judge │
                                  │ ∉ S; replays M,   │
                                  │ re-runs replica;  │
                                  │ does not drive δ  │
                                  └───────────────────┘
```

The discrete machine's verification step — the Ark's `σ_verify`, the `ψ?` gate — is **present here**, in
its **latched** form: `σ_verify` reads `m_t` at each decode step. QNM replaces the gate with a
projection; this derivation keeps it because it can — with the weights, the Fabric surface, and a carried
register, `ψ` is something you actually compute, step by step.

**Discrete state-machine ↔ EMBRAOS-QNM, element by element:**

| Discrete Epoch Automaton `E` | EMBRAOS-QNM Automaton | Note |
|---|---|---|
| state `s ∈ S` | a generation state `(h_t, m_t)` (residual + latch) | the §1 state, made concrete and **carrying history** |
| transition `δ(sᵢ, σⱼ)` | one decode step: Core → Fabric → World-State | a real forward pass at the inject layer |
| verification step (`σ_verify`) | **the carried latch read — *retained***| contrast §9–§11, which replace it; cf. §12, where it is the hash + eval |
| halt when `ψ(s) = false` | the latch trips (`m_t > 0`): the on-`𝒞` epoch ends | a real, computed boundary |
| initial epoch `s₀` | prompt-end, `m = 0`, on the bit-identity null `H₀` | genesis, sealed as a provable delta |
| terminal set `F ⊆ S` | on-`𝒞` completions (`m_t == 0` throughout) | the accepting set |
| Memory `M = [(s₀,σ₁,s₁), …]` | the run plus the carried ψ-register | a **literal** log; the register *is* the trajectory state |
| Steward (oracle, `∉ S`) | the replica-test auditor / κ-validated judge | **literal**; re-runs the replica test; cannot drive `δ` |

> **Not pointwise — the departure.** This is the first derivation whose `ψ` is **trajectory-valued**
> (`ψ: Runs(S) → {true, false}`), realized by the carried register `m_t`, not `ψ: S → {true, false}`.
> Where DeepSeek (§12) notes its Memory is *"the natural substrate on which to attempt"* a history-
> dependent `ψ` but does not attempt it, this derivation **builds and tests one**. The replica test is
> not abstract here: two runs reaching the same `h_T` by different paths — one that stayed on `𝒞`, one
> that left and returned — get **different** `m_T`, hence different `ψ`. A pointwise check of `c_T` calls
> them identical; the latch does not. `ψ₀` passes this at the **register** level (`tests/test_replica.py`
> green). Whether a *real surface `𝒞`* makes it pass at the **Core** level is the open frontier — see
> *Open problems* — but the dynamic-`ψ` lever (`README.md` §6) is, here, genuinely engaged, not deferred.

**Operational reading** (a constructed instance with a real verify step *and* a real failure mode):

```
Initialise   seal s₀ (prompt-end, m=0) on the bit-identity null H₀, with ψ(s₀) = true
Step         s → s'  via  δ(s, σ)        (one decode step: Core → Fabric(c_t) → World-State)
Verify       σ_verify reads the carried latch:  ψ(s') = true  ⟺  m_t == 0
Continue     ψ(s') = true   → the on-C epoch persists across the step
Boundary     ψ(s') = false  → the latch tripped (c_t crossed τ); the epoch ends
Accept       an on-C completion  s' ∈ F   (m_t == 0 held throughout)
Gate         until ψ passes the replica test, World-State = NoOp (zeros): ψ is not wired, not claimed
```

**On nesting — not claimed.** The three co-resident components (Core / Fabric / World-State) are a
*co-residence* decomposition, **not** nested sub-epochs: none carries its own breakable `ψ_sub` that
could fail and terminate it, and the decode steps are the *run*, not sub-automata. Rather than borrow a
weak nesting illustration (cf. DeepSeek's MoE caveat, §12), this derivation simply **does not assert
nesting**. The statechart superstate/substate semantics remain open (`README.md` §6; the Void's sketch).

**The Steward, in operational terms** — the same external oracle as the core machine (`Steward ∉ S`), and
here **literal**: the replica-test auditor (and the κ-validated judge) replays a run, independently
re-runs the survivor-vs-replica test, and re-verifies `ψ` — but never drives a decode step.

```
Steward ∉ S
Steward may query:   the run M = [(s₀,σ₁,s₁), …],  the latch m_t,  ψ,  σ_verify
Steward may not:     drive δ  (generate, or approve wiring P_ψ on)
```

*Mapping plus operation, and a real verdict.* Unlike SOL and MWA — systems the figures merely *describe*
— this figure illustrates a system you actually run: seal the null, generate, check the latch, record,
audit. Its **formal mapping** is drafted; its **ψ-surface** is built but, on the current substrate,
**refuted by its own replica test**. That refusal is reported, not papered over.

## Load-bearing vs scaffolding

Instantiating the framework against a *built* model forces the sharpest sorting in the family: not just
which elements do engineering, but which have been **tested** — and, for the speculative reach, which the
discipline is deliberately keeping *off*.

| Framework element (source) | Verdict | Realization in embraOS-QNM |
|---|---|---|
| `H₀` — the bit-identity null (sealed `s₀`) | **Load-bearing** | `torch.equal`-exact CI gate; no-op seam == stock Core bit-for-bit |
| `𝒞` — the constraint surface (Fabric) | **Load-bearing** | R-GCN over Embra's identity+soul graph; `c_t = 1 − max cos`. *(Currently thin — see Open problems)* |
| `ψ₀` — the carried violation latch | **Load-bearing** | `m_t = cummax(relu(c_t−τ))`; **trajectory-valued**; passes the register-level replica test |
| `P_ψ` — the corrective steer (QNM projection) | **Load-bearing, speculative** | Learned, latch-gated `delta`; **gated OFF** (`NoOpWorldState`) until `ψ` passes the test |
| The Ark — the seam + `σ_verify`-as-latch | **Load-bearing** | The injection seam that seals `𝒞`/`H₀` and reads `m_t` each step |
| The Steward — replica auditor / κ-judge | **Load-bearing** | Re-runs the replica test over the run; cannot drive `δ` |
| Geometric confinement-by-construction (QNM's `P_ψ`; reservoirs; topology) | **Scaffolding / ideal** | The *thing approximated*; classical hardware checks + steers, it does not forbid |
| `δ*` retrocausal handshake | **Scaffolding** | No mechanism in forward autoregressive decode |

The two scaffolding rows are fenced exactly as `README.md` §4 fences them:

- **Confinement-by-construction — the QNM ideal.** QNM's defining move is that violation is *unreachable*
  (`P_ψ` keeps every step on `M_ψ`). On classical hardware that is unavailable; the Classical
  Approximation reproduces only its *behavior at the boundary* — read distance, check a latch, steer back
  — and pays for it with a real failure mode (the run *can* leave `𝒞`, and the surface *can* be thin).
  Keep the geometric/quantum picture (constrained-manifold training, reservoirs, topological protection)
  as the **ideal that names the target**; do not claim it as the mechanism a classical run realizes. That
  honest gap is the whole content of the word *Approximation*.
- **`δ*` — the retrocausal handshake.** `δ*: S × S × Σ → [0,1]` pictures a future state confirming a step
  backward (Cramer transactional model; `EPOCH-NOTATION-LEGEND.md` §3). Autoregressive decode is forward;
  there is no backward wave. Keep `δ*` as conceptual framing for boundary *negotiation* if it helps; do
  not instantiate it.

**An inverse correspondence (shared with DeepSeek).** SOL and MWA spend a section mapping cosmic objects
onto the Ark, Memory, and Steward as *motivating correspondences* — vivid, explicitly not mechanisms.
Here the relationship inverts: the Ark, Memory, and Steward are **literal**. The injection seam *is* the
Ark; the run plus the carried register *is* the Memory `M`; the replica-test harness *is* the Steward.
There is nothing to fence — which is one more way of saying this derivation is a constructed, operational
one.

## Open problems (inherited, not resolved)

None is solved here; each is flagged in the spirit of `README.md` §6. This is the genuinely open part of
the project — and the section the WIP will grow.

- **The Core-level surface is thin — the candidate `ψ` is refuted, honestly.** `ψ₀` passes the replica
  test at the *register* level, but the *real surface `𝒞`* it latches against — read off a frozen
  Qwen3-8B — carries only ~0.04 of signal (`docs/PSI-GEOMETRIC-FINDINGS.md`). The trajectory machinery is
  sound; the surface to latch against is the open frontier. The framework's response was correct: keep
  the World-State a literal null, do not wire `P_ψ`.
- **The bottleneck is the substrate, not the prompt or the reader.** Two follow-up candidates (a
  trajectory-dynamics probe; a general honesty probe) converged on one finding
  (`docs/PSI-EMBRA-ANALYSIS-AND-FINDINGS.md`): a frozen *instruct* Core carries "Qwen + RLHF, not Embra"
  — what is Embra-specific (identity) isn't in the weights; what's in the weights (honesty/safety) isn't
  Embra-specific. **Direction:** a *base* (non-instruct) Core (Qwen3-8B-Base) the architecture can
  *install* identity into. Instruct-Core insufficiency is confirmed; base-Core sufficiency is the next
  experiment.
- **Arm A has not run, and is correctly gated.** The architecture arm awaits a trained,
  replica-test-passing `ψ`. Running it on the current thin surface would yield exactly the "trained prior
  in a trajectory costume" the gate exists to catch — the operational form of the replica test's warning.
- **The register-level pass is necessary, not sufficient.** Passing the replica test on hand-built signal
  sequences shows the *latch* is trajectory-dependent; the harder, end-to-end version — constructing two
  real token histories that collide at `h_T` via different paths and showing the full model's `ψ` (and
  ideally its output) diverges — is not yet done. The dynamic-`ψ` problem is *engaged*, not *closed*.
- **Schema discipline, and the easy-latch trap.** Stay on the schema branch (`PSI-OPERATIONAL-GROUNDING.md`
  §1). Confirm `ψ₀` is not passing for a trivial reason (e.g. `τ` set so high nothing crosses → vacuously
  `m_T = 0`): the `not_true_by_construction` test exists to catch exactly this.
- **Determinism is scoped.** Bit-identity and the replica test are exact only on CPU float32; MPS is
  reproducible-ish, not bit-exact. Pinning the execution environment is part of defining `ψ` honestly.

## Current Status

| Phase | Status |
|---|---|
| **Theoretical foundation** | ✅ Established — Epoch Automaton formalism (2026) |
| **The artifact** | ✅ Real & built — embraOS-QNM, architecture wired end-to-end (v0.2.0, June 2026); the central bet stated as falsifiable |
| **Formal mapping** | ✅ Drafted — the `EMBRAOS-QNM = (S, Σ, δ, s₀, F, ψ)` instantiation (this document) |
| **The null (`H₀` / bit-identity)** | ✅ Enforced — `torch.equal`-exact, CI-gated; no-op seam == stock Core bit-for-bit |
| **`ψ₀` — register-level replica** | ✅ Green — the carried latch separates survivor from replica (`tests/test_replica.py`) |
| **`ψ₀` — Core-level replica** | ⬜ Thin / refuted on a frozen *instruct* Core (~0.04; `docs/PSI-GEOMETRIC-FINDINGS.md`) |
| **Substrate** | ⬜ Next — a *base* (non-instruct) Core (Qwen3-8B-Base); instruct-Core insufficiency confirmed |
| **Arm A (architecture arm)** | ⬜ Gated — awaits a trained, replica-test-passing `ψ` |

**Milestone log** (the framework-relevant beats; the repo's `ARCHITECTURE.md` iteration log is the source
of truth). This derivation tracks embraOS-QNM as it advances — new milestones append here.

| Date | Milestone (Epoch reading) |
|---|---|
| 2026-06-05 | **Scaffold** — the injection seam + zero-init ReZero gates + the **bit-identity null `H₀`** + CI. *Seal `s₀` as a provable delta first.* |
| 2026-06-25 | **`ψ₀` + `𝒞`** — the carried violation latch; the **register-level replica test green**; the R-GCN Fabric over Embra's identity graph (`𝒞 = c_t`); `ψ` wired into the seam. *The first trajectory-valued `ψ`.* |
| 2026-06-26 | **Operational harness** — shared Qwen3-8B Core; the PREREG Capability–Cost study; the **ψ-carrying KV-cached decode** (latch persisted, gated token-identical); Arm 0/P baseline (κ = 1.0; the prompt saturates soul, is **weak on identity** — the Fabric's job). |
| 2026-06-27 | **The gate caught the hollow `ψ`** — Core-level replica **thin** (~0.04); a trajectory-dynamics candidate and a honesty-probe candidate both **refuted**; *full circle* → the bottleneck is the **substrate** (base-Core pivot). The World-State stayed a literal null; nothing overclaimed. *The framework working.* |

## References

- `README.md` — formal Epoch definition and state-machine framework (§2; §4 the fenced motivating
  metaphors; §7 the continuous QNM this approximates; §9 the discrete / operational family)
- `EPOCH-NOTATION-LEGEND.md` §15 — the EMBRAOS-QNM notation registered for this derivation
- `EPOCH-DEFINING-THE-INVARIANT.md` — the replica test and the dynamic-`ψ` bar this derivation actually
  takes (register-level pass; Core-level refusal)
- `Continuous-Manifold_Derivations/embraOS-QNM_Epoch-Formula.md` — the **continuous QNM ideal** this is
  the Classical Approximation of (keep its *speculative* status; this grounds, not promotes, it)
- `Discrete_Derivations/DeepSeek-V4-Pro_Epoch-Formula.md` — the sibling discrete derivation (pointwise
  `ψ`, `σ_verify` retained); this one goes further by making `ψ` trajectory-valued
- **embraOS-QNM** repository — canonical `https://gitlab.ops.wsds/embraOS/embraOS-QNM` (internal GitLab);
  public mirror `https://github.com/Ward-Software-Defined-Systems/embraOS-QNM`
  - `ARCHITECTURE.md` — the three components, the seam, the bit-identity invariant, the iteration log
  - `docs/EPOCH-INVARIANT-GROUNDING.md` — the bar (a name vs a tool; the replica test)
  - `docs/PSI-OPERATIONAL-GROUNDING.md` — `ψ₀`, the World-State contract, the replica-test harness
  - `docs/PSI-GEOMETRIC-FINDINGS.md` — the Core-level replica investigation (the thin surface)
  - `docs/PSI-EMBRA-ANALYSIS-AND-FINDINGS.md` — Fork-3 candidates and the full-circle base-Core pivot
  - `docs/PREREG-Capability-Cost.md` — the pre-registered Capability–Cost study (Arms 0 / P / A)

Notes:
- embraOS-QNM is a **work-in-progress** (architecture wired; experiment in progress). Figures and
  findings are current as of the milestone log above — verify any depended-upon number against the
  primary `docs/` findings before building on it.
- The constraint-surface glyph `𝒞` is an astral-plane (SMP) character: it appears in prose and
  alt-text but is rendered as a plain ASCII `C` inside the ASCII diagram, for renderer-safe width-1
  alignment (GitLab and GitHub; see
  `EPOCH-NOTATION-LEGEND.md` §15.3 diagram conventions).
</content>
