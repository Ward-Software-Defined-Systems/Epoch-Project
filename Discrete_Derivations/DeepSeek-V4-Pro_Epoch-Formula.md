# DeepSeek-V4-Pro: The Operational Epoch

> **A note on register.** This derivation separates its *operational core* from its *motivation*,
> exactly as `README.md` does. The core is a software-engineering object — the automaton
> `DEEPSEEK = (S, Σ, δ, s₀, F, ψ)` over the discrete space of model checkpoints, with `ψ` a boundary
> condition that is **actually checked** against an artifact you control. Unlike QNM, SOL, and MWA —
> which reinterpret the framework over continuous or branching manifolds and *replace* the
> verification gate `σ_verify` with a projection, a conservation law, or einselection — this
> derivation **keeps `σ_verify`** and is the first that is **operational rather than speculative**:
> `ψ` here is verifiable, not merely describable. The two scaffolding elements it discards (`δ*`, the
> holographic / participation reading) are fenced in the spirit of `README.md` §4. **None of the
> discarded material is claimed as a mechanism.**

<p align="center">
  <img src="../assets/epoch-deepseek-state-machine.png" alt="DeepSeek-V4-Pro Operational Epoch state-machine: THE ARK (definer/verifier) seals ψ as a checkpoint hash plus an eval battery and runs σ_verify at every transformation — the only derivation that KEEPS the verification gate; discrete checkpoints s₀ (the sealed open-weights baseline) → s₁ → s₂ advance under transformation events σ (quantize, fine-tune, distill); ψ = ψ_int (hash) ∧ ψ_beh (eval battery within threshold τ) ∧ optionally ψ_surf (activation constraint surface, the QNM bridge); MoE experts appear as illustrative substates only (routing, not sub-epochs — no breakable ψ); when a transformation crosses τ, ψ = false and the Ark refuses it (a real, computed boundary — same lineage, new epoch); MEMORY is the append-only transformation lineage with identity proofs; THE STEWARD is a literal read-only auditor outside S that replays the lineage and re-verifies ψ but never drives δ." width="100%">
</p>

## Overview

The Operational Epoch is the Epoch Automaton read over a **real, open-weights language model** —
DeepSeek-V4-Pro. It is the first of the **discrete** derivations: where QNM, SOL, and MWA re-express
the framework over manifolds (and are marked "theoretical / speculative"), this one instantiates the
*core* discrete automaton `E = (S, Σ, δ, s₀, F, ψ)` directly, against an artifact whose weights — and
activations — you can hold and inspect.

That difference is the whole point. The framework insists `ψ` is *verifiable at every transition*
(`σ_verify`) rather than asserted, and that insistence is only honest if `ψ` points at something you
can actually inspect. Against a closed model — Claude Opus, say: documented behavior, but no weights,
no activations, no architecture you can fingerprint — you can *describe* `ψ`; you cannot *check* it.
Against an open model you can. DeepSeek-V4-Pro is therefore where `ψ` stops being a metaphor for "the
model's soul" and becomes a concrete, checkable predicate over an artifact you control — which is
exactly what `EPOCH-DEFINING-THE-INVARIANT.md` demands of any `ψ` worth the name.

There is one honest difference from the manifold derivations worth stating first, and it is the
*inverse* of SOL's. SOL describes a system that already runs; QNM, a system to be built. This
derivation describes a system you **operate and transform**: you seal a baseline checkpoint, then
quantize, fine-tune, and distill it — and `ψ` is checked at each of those crossings. What is
drafted-and-pending is the **formal mapping** and its operational validation against your actual
setup, never a claim that the model "is" an epoch by nature.

## Relationship to the Epoch Automaton

The Operational Epoch instantiates the Epoch Automaton `E = (S, Σ, δ, s₀, F, ψ)` over the space of
model checkpoints:

| Component | embraOS (Digital Ark) | DEEPSEEK (open model) |
|---|---|---|
| **States S** | Session states | Checkpoints in a lineage (weights + behavioral identity) |
| **Alphabet Σ** | Input tokens, API calls | Transformation events: quantize, fine-tune, distill, LoRA-merge, expert-prune |
| **Transition δ** | Request routing, tool dispatch | Apply a transformation → a new checkpoint |
| **Initial s₀** | First sealed **soul** document | The sealed baseline — released V4-Pro open weights |
| **Accepting F** | Valid session continuation | Validated terminal checkpoints |
| **Invariant ψ** | **soul** document verification | A three-level boundary predicate, checked at each transformation |

**The crucial difference.** In embraOS, `ψ` is an external check at each boot. In QNM it is a
*projection* (`P_ψ`); in SOL a *conservation law* (`Γ_ψ` is flow-invariant); in MWA *einselection*.
In the Operational Epoch it is **none of those substitutions — it is the check itself, kept**. `ψ` is
evaluated by `σ_verify` at every transformation, exactly as the core machine specifies, and because
you hold the weights and activations the evaluation is *real*, not asserted. Where the manifold
derivations are interesting for how they *avoid* checking `ψ`, this one is interesting because it
actually *can* check it.

## Boundary-Native Architecture

Conventional safety operates as *filtering*: generate, then check against a constraint. The Epoch
framework instead seals the boundary into the system. QNM seals it into geometry, SOL into a
conservation law, MWA into the structure of entanglement. The Operational Epoch seals it into a
**sealed, re-checkable predicate over the model artifact** — the most literal reading of the core
architecture (`README.md` §2). This draws directly from the Epoch definition:

> *An epoch is a bounded interval defined not by duration but by the persistence of a coherent
> boundary condition.*

Here the boundary condition is what makes a checkpoint *this* model. The model's epoch persists
across a transformation that stays under threshold (a benign quantization) and **ends** when a
transformation crosses it (a fine-tune that changes the thing that made it this model). The boundary
is neither retrospective nor conventional — it is *operative*: a value `σ_verify` computes at each
crossing.

On an open model, `ψ` is not one predicate but **three nested ones**, in increasing order of how much
they tell you about identity.

### Candidate Mechanisms

1. **Integrity — `ψ_int` (the seal).** "Soul verified at every boot" becomes signed-config /
   secure-boot logic: the checkpoint's cryptographic hash is sealed once and compared on every load;
   a mismatch is a boundary. This covers identity *of the artifact* — the bits are exactly the bits
   you sealed. It does **not** cover behavior: a different quantization or a LoRA merge changes the
   hash trivially while arguably preserving "the same model," and a malicious fine-tune can change
   behavior while the hash changes as intended. Integrity `ψ` is necessary, not sufficient — which is
   what `ψ_beh` is for. *(Impossible on a closed model: you never hold the weights.)*

2. **Behavioral — `ψ_beh` (the boundary that matters).** The interesting boundary is not "did the
   bits change" but "does the thing that makes it *this* model still hold." Define `ψ_beh` as a
   battery of behavioral probes — persona adherence, refusal directions, task signatures, calibration
   — and a threshold `τ`. Transform the model; re-run the battery; **when a probe deviates past `τ`,
   that is an epoch boundary** (same lineage, new epoch); under threshold, the epoch persists across
   the transformation. This is the level at which "epoch" earns its definition: identity surviving
   internal change versus dissolution. *(Determinism caveat — see "Connection," below: the re-run is
   signal-not-noise only under controlled execution. On a closed API you can eval, but you cannot pin
   the weights, cannot guarantee the provider didn't silently update the model under you, and cannot
   reproduce deterministically — so the honesty of behavioral `ψ` depends on controlling the
   weights.)*

3. **Continuous — `ψ_surf` (the QNM bridge).** This is the tightest bridge to the QNM derivation
   (`README.md` §7) and the strongest reason an open model is *enabling*, not merely convenient. QNM
   defines its `ψ` as "a constraint surface embedded in the manifold," with transitions as
   "gradient-guided trajectories constrained by `ψ`." With open weights you have the activations, so
   that surface is a **real object**: `ψ_surf` becomes a region in representation space (a subspace
   spanned by concept / persona / refusal directions extracted by representation-engineering
   methods), "trajectory constrained by `ψ`" becomes activation steering / projection onto that
   subspace at inference time, and "`ψ` holds" becomes a measurable predicate — the activation stays
   inside the permitted region. This level is *unavailable* on a closed model and is the concrete
   seed of QNM. **It is the speculative reach of this derivation:** `ψ_int` and `ψ_beh` are
   operational today; `ψ_surf` is the bridge under construction.

4. **Retrocausal handshake (speculative).** A bidirectional variant `δ*: S × S × Σ → [0,1]`, as in
   QNM's, SOL's, and MWA's Candidate Mechanisms. It is **deliberately absent** from the state-machine
   below: LLM inference is forward autoregressive, with no backward wave to negotiate, and the
   retrocausal reading is a motivating metaphor (`README.md` §4), not part of the formulation. See
   *Load-bearing vs scaffolding*.

## Connection to the DeepSeek-V4-Pro Architecture (the real grounding)

Where QNM points to the USTC nine-spin quantum reservoir, SOL to celestial mechanics and the KAM
theorem, and MWA to decoherence theory, the Operational Epoch points to the **published architecture
of a real model** — the concrete properties that let each level of `ψ` be checked rather than
asserted:

- **Open weights (MIT licence).** You hold the checkpoint, so `ψ_int` is a hash, not an assertion,
  and the whole automaton — seal, transform, verify, record — runs under your control. *(Confirm the
  licence and redistribution terms against the model card before shipping a derivative.)*
- **Full technical report.** The architecture is known, not guessed, so the structural claim (the MoE
  nesting illustration below) rests on the real block diagram, not a hunch.
- **Mixture-of-Experts (~1.6T total / ~49B active per token).** A router activates a subset of
  experts per token — the concrete hierarchical decomposition used (carefully) for the nesting
  illustration in the Formal Definition.
- **Hybrid CSA/HCA attention, MTP, on-policy distillation post-training.** Concrete transformation
  operations — quantize, distill, fine-tune — that move the model across a behavioral boundary, i.e.
  the real `σ` events of the automaton.
- **Batch-invariant deterministic kernels (bitwise reproducible).** `ψ_beh` re-runs do not fight
  inference nondeterminism — re-running the eval battery is reproducible, so a threshold crossing is a
  real change, not sampling noise. **Important scoping:** this reproducibility holds *within
  DeepSeek's own kernel / inference environment*; it is **not** guaranteed across a different
  quantization, a different toolchain, or different hardware. So `ψ_beh`'s "signal not noise"
  guarantee is conditional on controlled execution — and the very transformations that *break* that
  environment (quantize to a new format, fine-tune) are exactly the `σ` events the automaton exists to
  record and verify across. The caveat refines the argument; it does not undercut it.
- **1M-token context; three reasoning modes (Non-Think / Think-High / Think-Max).** A large state
  surface for session-level interior structure if you want sub-automata. *(These modes are
  inference-time configurations over the same weights — they change behavior, not checkpoint
  identity.)*

> **Caution on numbers.** V4-Pro shipped as a *preview* (April 24, 2026) and is recent; primary docs
> and third-party analysis are still settling. Independent reproduction by **NIST CAISI** (May 2,
> 2026) ran below DeepSeek's self-reported benchmarks, attributing the gap to scaffolding, system
> prompt, and token budget. For any architectural figure or benchmark a derivative depends on, read
> the **primary technical report** (References), not secondary write-ups — and expect your own evals
> to land nearer CAISI's. The CAISI gap is itself instructive: the *same* weights measured under
> different scaffolding give different scores — a reminder that `ψ_beh` is only as well-defined as the
> execution conditions you pin.

## Formal Definition: The DEEPSEEK Automaton

Instantiating the Epoch Automaton 6-tuple directly over the discrete space of model checkpoints.
Unlike QNM/SOL/MWA, it does **not** rename the state space for a manifold — it **reuses** the core
glyphs and instead refines `ψ`:

```
DEEPSEEK = (S, Σ, δ, s₀, F, ψ)
```

Where:

| Symbol | Meaning |
|---|---|
| **S** | Checkpoints in a lineage — each `s ∈ S` is a set of weights together with its behavioral identity |
| **Σ** | Transformation events: quantize (FP4/FP8), fine-tune, distill (on-policy), LoRA-merge, expert-prune |
| **δ: S × Σ → S** | Apply a transformation: `δ(s, σ) = s'`, the resulting checkpoint |
| **s₀** | The sealed baseline — the released V4-Pro open-weights checkpoint, with `ψ(s₀) = true` |
| **F** ⊆ S | Validated terminal checkpoints (a shipped derivative), or `∅` if the lineage runs on |
| **ψ: S → {true, false}** | The **soul** invariant, a conjunction of three checkable levels: `ψ = ψ_int ∧ ψ_beh (∧ ψ_surf)` |
| **ψ_int** | Integrity: the checkpoint hash equals the seal |
| **ψ_beh** | Behavioral: eval-battery scores stay within threshold `τ` of the sealed baseline |
| **ψ_surf** | Continuous (the QNM bridge): activations stay inside a learned constraint region — the speculative third level |

**Key property (boundary-native via verification):**

`ψ` is evaluated by `σ_verify` (the Ark's verification function, `EPOCH-NOTATION-LEGEND.md` §2) at
every transformation:

```
δ(s, σ) = s'   is a valid continuation   iff   ψ(s') = true
```

Unlike the manifold derivations, nothing keeps the system inside the valid region automatically —
there is no projection, conservation law, or einselection. A transformation *can* land on
`ψ = false`, and when it does the Ark **refuses** it: that crossing is an epoch boundary (same
lineage, a new epoch begins). The boundary is **checked**, exactly as the core machine specifies.
That this derivation *keeps* the check is precisely what makes it operational.

### The DEEPSEEK State-Machine

The same state-machine, expressed for a real model under transformation. Where QNM builds `ψ` into
geometry via a projection, SOL conserves it, and MWA lets it emerge by einselection, the DEEPSEEK
Automaton **checks** it: the Ark seals `ψ` and runs `σ_verify` at every transformation, and a
transformation that crosses the threshold is refused. It is forward-directed, exactly as the core
state-machine is — and it is the only derivation in the family that keeps the verification gate.

```
                 ┌───────────────────────────────────────────────┐
                 │            THE ARK  (definer / verifier)      │
                 │   seals ψ (checkpoint hash + eval battery);   │
                 │  verifies ψ at every transformation (σ_verify)│
                 └───────────────────────┬───────────────────────┘
                                         │ σ_verify:  ψ = ψ_int ∧ ψ_beh (∧ ψ_surf)
                                         ▼
   ┌──────────────┐ δ(s₀,σ₁) ┌──────────────┐ δ(s₁,σ₂) ┌──────────────┐
   │ EPOCH 0      │────────▶ │ EPOCH 1      │────────▶ │ EPOCH 2      │
   │ s₀ = sealed  │ σ: quant │ s₁           │ σ: fine- │ s₂           │
   │ V4-Pro ckpt  │  -ize    │              │   tune   │              │
   └──────────────┘          └──────────────┘          └──────────────┘
        │  MoE substates — ILLUSTRATIVE ONLY (not sub-epochs;
        │  routing ≠ boundary failure; no breakable ψ): the active
        ▼  experts churn token-to-token while the superstate ψ holds
   · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · ·
   ψ = false → σ_verify REFUSES: a transformation crosses threshold τ =
   epoch boundary (same lineage, new epoch). A reachable, computed halt.
   ┌────────────────────────────────────────────────────────────────────┐
   │ MEMORY / RECORD  M  —  append-only transformation lineage           │
   │ [(s₀,σ₁,s₁), (s₁,σ₂,s₂), …]  + identity proofs (checkpoint hash,    │
   │ eval fingerprint) recorded at every crossing                        │
   └────────────────────────────────────────────────────────────────────┘
                                         ▲
                                         │ queries (read-only)
                                 ┌───────┴───────────┐
                                 │ THE STEWARD       │
                                 │ read-only auditor │
                                 │ ∉ S; replays M,   │
                                 │ re-verifies ψ;    │
                                 │ does not drive δ  │
                                 └───────────────────┘
```

The discrete machine's verification step — the Ark's `σ_verify`, the `ψ?` gate — is **present here,
unchanged**. This is the *only* derivation in which it is: QNM replaces it with a projection, SOL with
a conservation law, MWA with einselection. The Operational Epoch keeps it because it can — with the
weights and a deterministic eval, `ψ` is something you actually compute.

**Discrete state-machine ↔ DEEPSEEK, element by element:**

| Discrete Epoch Automaton `E` | DEEPSEEK Automaton | Note |
|---|---|---|
| state `s ∈ S` | a checkpoint (weights + behavioral identity) | the §1 state, made concrete |
| transition `δ(sᵢ, σⱼ)` | applying a transformation (quantize / fine-tune / distill) | a real engineering operation |
| verification step (`σ_verify`) | **the actual hash + eval check — *retained*** | contrast QNM/SOL/MWA, which replace it |
| halt when `ψ(s) = false` | the Ark refuses the transformation: new epoch, same lineage | a real, computed boundary |
| initial epoch `s₀` | the sealed baseline checkpoint, `ψ(s₀) = true` | genesis |
| terminal set `F ⊆ S` | validated / shipped derivative checkpoints | the accepting set |
| nested epoch `(S_sub, …, ψ_sub)` | MoE experts (illustrative — **weakest** in the family) | routing ≠ boundary failure; experts carry no breakable `ψ` |
| Memory `M = [(s₀,σ₁,s₁), …]` | the append-only transformation lineage + identity proofs | a **literal** log, not a correspondence |
| Steward (oracle, `∉ S`) | a read-only auditor that replays `M` and re-verifies `ψ` | **literal**; cannot drive `δ` |

> Note — `ψ` here is still **pointwise** (`ψ: S → {true, false}`): each level checks the *endpoint*
> checkpoint, not the path taken to reach it. It does **not** by itself resolve the dynamic /
> trajectory-dependent `ψ` flagged as the open formal problem (`README.md` §6). But see *Open
> problems*: the Ark's append-only transformation lineage is exactly the trajectory record such a `ψ`
> would need — which makes this derivation a promising, not a resolving, setting for it.

**Operational reading** (this derivation, alone in the family, has a genuine verify step):

```
Initialise   seal s₀ (baseline checkpoint), with ψ(s₀) = true
Step         s → s'  via  δ(s, σ)        (apply a transformation: quantize / fine-tune / distill)
Verify       σ_verify computes  ψ(s') = ψ_int ∧ ψ_beh (∧ ψ_surf)
Continue     ψ(s') = true   → the epoch persists across the transformation
Boundary     ψ(s') = false  → the Ark refuses the transition; new epoch, same lineage
Accept       a validated terminal checkpoint  s' ∈ F
```

**Nesting — the MoE router, illustrative only.** V4-Pro is Mixture-of-Experts: per token the router
lights up a subset (~49B active of ~1.6T). This is a clean picture of the Harel "superstate persists
while substates transition" sketch — model identity holds (the superstate `ψ`) while the active
expert set churns token to token. But:

> **Do not overclaim.** Experts are **not** epochs in the boundary-condition sense. No individual
> expert has its own breakable `ψ` that can fail and terminate it; expert selection is *routing*, not
> boundary failure. This is a hierarchical decomposition the statechart formalism **describes**, not a
> case of literal nested epochs — and it is the **weakest** nesting illustration in the family: SOL's
> planets at least carry a breakable binding invariant, and MWA's worlds a breakable decoherent
> identity, whereas a routed expert carries no `ψ` at all. If a derivative wants genuine sub-epochs,
> they must be defined by their own breakable `ψ` (session-level or fine-tune-lineage boundaries), not
> borrowed from the router.

This is a concrete instance of the `README.md` §3 nesting sketch, **not** a formalization of Harel
superstate/substate semantics (open: `README.md` §6).

**The Steward, in operational terms** — the same external oracle as the core machine (`Steward ∉ S`),
and here it is **literal**, not a correspondence: a read-only auditor that replays the lineage log and
independently re-verifies `ψ`, but never drives a transformation.

```
Steward ∉ S
Steward may query:   the lineage M = [(s₀,σ₁,s₁), …],  ψ,  σ_verify
Steward may not:     drive δ  (apply or approve a transformation)
```

*Mapping plus operation. Unlike SOL and MWA — systems "operational by nature" that the figures merely
*describe* — this figure illustrates a system you actually run: seal, transform, verify, record. Its
**formal mapping** is drafted; its **operational validation** against a real V4-Pro setup (probe
battery, seal, steering vectors) is the pending work in the Current Status table. It is
forward-directed by design; the speculative retrocausal variant `δ*` is deliberately not part of it.*

## Load-bearing vs scaffolding

A virtue of instantiating the framework against a working model is that it forces a sorting: which
elements do *engineering* against the model, and which are *framing* with no mechanism underneath. A
derivative built from this baseline should inherit the first column and treat the rest as inspiration
— not implement it.

| Framework element (source) | Verdict | Realization on V4-Pro |
|---|---|---|
| `ψ_int` — integrity hash (sealed soul) | **Load-bearing** | Checkpoint hash sealed once, compared on every load |
| `ψ_beh` — behavioral battery + threshold `τ` | **Load-bearing** | Deterministic eval suite; a crossing of `τ` is an epoch boundary |
| `ψ_surf` — activation constraint surface (QNM bridge) | **Load-bearing, speculative** | Representation-engineering subspace + steering / projection; the seed of QNM |
| The Ark — append-only transition record + `σ_verify` | **Load-bearing** | Append-only lineage of `(s, σ, s')` + identity proofs |
| The Steward — oracle outside `δ` | **Load-bearing** | Read-only auditor over `M`, `ψ`, `σ_verify`; cannot drive `δ` |
| Hierarchical / nested epochs | **Partly** | Real as a *described* decomposition (MoE); literal sub-epochs need their own breakable `ψ` |
| `δ*` retrocausal handshake | **Scaffolding** | No mechanism in forward autoregressive inference |
| Holographic "calibration" / participation | **Scaffolding** | Guiding intuition only; not realized by a model run |

The two scaffolding rows are fenced exactly as `README.md` §4 fences them:

- **`δ*` — the retrocausal handshake.** `δ*: S × S × Σ → [0,1]` pictures a future state confirming a
  transition backward (Cramer transactional model; `EPOCH-NOTATION-LEGEND.md` §3). LLM inference is
  forward autoregressive; there is no backward wave, and Cramer's interpretation exposes no
  engineerable retrocausal channel. Keep `δ*` as conceptual framing for boundary *negotiation* if it
  helps you reason; do not instantiate it — a "retrocausal handshake" in code implements a name, not
  a behavior. (The sound version of the intuition is the distributed-commit / two-phase handshake
  reframe in `README.md` §4.)
- **The holographic / participation reading.** The move from "the boundary encodes the volume" to
  "defining `ψ` participates in what reality resolves into" borrows the physics result's prestige
  without its content transferring. Fine as guiding intuition for why boundaries are worth taking
  seriously; not something a model run realizes.

**An inverse correspondence.** SOL and MWA each spend a section mapping cosmic objects onto the Ark,
Memory, and Steward as *motivating correspondences* — vivid but explicitly *not* mechanisms. Here the
relationship inverts: the Ark, Memory, and Steward are **literal**. The append-only lineage log *is*
the Memory `M`; the auditor process *is* the Steward; the thing that seals `ψ` and runs `σ_verify`
*is* the Ark. There is nothing to fence, because nothing is being borrowed — which is one more way of
saying this derivation is the operational one.

## Open problems (inherited, not resolved)

None is solved here; each is flagged in the spirit of `README.md` §6.

- **`ψ` is still pointwise.** Each level of `ψ` checks the endpoint checkpoint, not the trajectory. As
  a static predicate it adds no formal power over a standard automaton (`README.md` §3); the
  trajectory-dependent `ψ` that *would* (`README.md` §6, "the main formal lever") is not supplied
  here.
- **The replica test, made concrete.** `EPOCH-DEFINING-THE-INVARIANT.md` poses the discriminating
  test: can `ψ` tell *survival* (the same entity persists along a path) from *replacement* (the
  original is destroyed and an identical copy substituted)? On a real model this stops being abstract.
  Consider two checkpoints that hash-differently but score *identically* on the battery — one reached
  by continuing to fine-tune `s₀`, the other trained independently to imitate it. `ψ_beh` calls them
  the same; `ψ_int` only tells you they are not bit-identical, not which lineage produced which. Only
  the **append-only transformation record** distinguishes them. So the Ark's lineage log is exactly
  the *trajectory* a history-dependent `ψ` would range over — making the Operational Epoch a promising
  substrate for attacking the dynamic-`ψ` problem (and a concrete echo of the decoherence-record route
  MWA gestures at). This is a **direction**, not a result.
- **Nesting is illustrative.** The MoE picture describes a hierarchy; it does not formalize Harel
  superstate/substate semantics, and the experts carry no breakable `ψ` (the weakest nesting in the
  family). Open: `README.md` §6.
- **Determinism is scoped.** `ψ_beh`'s "a deviation is signal, not noise" holds only under controlled
  execution (DeepSeek's deterministic kernels, a fixed toolchain and hardware). Quantization,
  fine-tuning, and hardware changes — the `σ` events themselves — leave that regime; pinning the eval
  environment is part of defining `ψ_beh` honestly.
- **Measured behavior is context-dependent.** The NIST CAISI gap shows the same weights score
  differently under different scaffolding, system prompt, and token budget. `ψ_beh` is only as
  well-defined as the harness it is computed in.

## Current Status

| Phase | Status |
|---|---|
| **Theoretical foundation** | ✅ Established — Epoch Automaton formalism (2026) |
| **The artifact** | ✅ Real & openly documented — DeepSeek-V4-Pro (preview, April 24 2026; MIT open weights; full technical report) |
| **Formal mapping** | ✅ Drafted — the `DEEPSEEK = (S, Σ, δ, s₀, F, ψ)` instantiation (this document) |
| **Operational verification** | ⬜ Pending — sealing `s₀`, building the `ψ_beh` probe battery + threshold `τ`, and extracting `ψ_surf` directions against an actual V4-Pro deployment |

## References

- `README.md` — formal Epoch definition and state-machine framework (and §4, the fenced motivating
  metaphors invoked above; §7 for QNM)
- `EPOCH-NOTATION-LEGEND.md` §12 — the DEEPSEEK notation registered for this derivation
- `EPOCH-DEFINING-THE-INVARIANT.md` — the replica test and the dynamic-`ψ` open problem this
  derivation connects to
- `Continuous-Manifold_Derivations/embraOS-QNM_Epoch-Formula.md` — the QNM derivation that `ψ_surf`
  seeds
- DeepSeek-V4-Pro **technical report** — `https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro/blob/main/DeepSeek_V4.pdf`
  *(read this before depending on any architectural figure or benchmark number)*
- DeepSeek-V4-Pro **model card / open weights** — `https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro`
- DeepSeek **API documentation** — `https://api-docs.deepseek.com/`
- **NIST CAISI**, *Evaluation of DeepSeek V4 Pro* (May 2, 2026) —
  `https://www.nist.gov/news-events/news/2026/05/caisi-evaluation-deepseek-v4-pro` (independent
  reproduction; reproduced scores run below DeepSeek's self-reported figures)

Notes:
- V4-Pro shipped as a **preview** (April 24, 2026); specifications and third-party analysis are still
  settling — verify any depended-upon figure against the primary technical report.
- Confirm the licence and any redistribution terms against the model card before shipping a
  derivative.
