# Many-Worlds: The Universal-Wavefunction Epoch

> **A note on register.** This derivation separates its *rigorous core* from its *motivation*,
> exactly as `README.md` does. The core is a standard-quantum-mechanics object — the automaton
> `MWA = (ℋ, Ĥ, U, Ψ₀, F_ℋ, ψ)` over Hilbert space, with unitary Schrödinger evolution and
> environment-induced decoherence. The interpretive role-assignments — the **universal
> wavefunction** as the Ark, the **relative-state record** as Memory, the **in-branch observer**
> as the Steward — are **motivating correspondences**, fenced in the spirit of `README.md` §4.
> Unlike QNM and SOL, here the fencing is *forced*: the Everett interpretation has no "outside,"
> so the Ark and Steward cannot sit external to the system in the way the core framework asks.
> **None of the correspondences is claimed as a physical mechanism.**

<p align="center">
  <img src="../assets/epoch-mwa-state-machine.png" alt="MWA Many-Worlds Epoch state-machine: the universal wavefunction Ψ with Schrödinger dynamics as the Ark (a fenced correspondence — MWI has no 'outside', and unitary evolution never rejects); Hilbert space ℋ with the universal wavefunction as Epoch 0 (superstate) under complex unitary flow U, then branching at a decoherence event into worlds (sub-epochs), each carrying a Born weight |c_k|² and its own decoherent-identity invariant ψ_sub^k, settling into the einselected quasi-classical set F_ℋ; the ψ=false analogue is recoherence, astronomically rare; Memory as a forking tree of branch-relative records; the Steward as an in-branch observer that itself branches." width="100%">
</p>

## Overview

The Universal-Wavefunction Epoch is the Epoch Automaton read over the **Many-Worlds (Everett)
interpretation** of quantum mechanics. It is the first of the **branching-manifold** derivations
— distinct from the continuous-manifold derivations (QNM, SOL) in three ways that, together, make
it a different kind of object:

- **The flow is complex.** Where QNM's `∇` (gradient) and SOL's `Φ_H` (symplectic) are real, the
  transition here is the **Schrödinger equation** `iℏ ∂Ψ/∂t = ĤΨ` — a complex differential
  equation whose `i` is exactly what makes the evolution *unitary* (norm-preserving).
- **The trajectory branches.** QNM and SOL each confine a *single* trajectory to an invariant
  region. Many-Worlds does the opposite: the universal wavefunction never collapses, and
  decoherence splits it into a growing *tree* of quasi-classical worlds.
- **The Ark has no "outside."** In MWI every observer is a subsystem of the universal wavefunction
  and branches with it. The framework's external Ark/Steward cannot sit outside the system — see
  the fenced correspondences and the open problems below.

As with SOL, this document *describes a system that already runs* rather than one to be built. What
is drafted-and-pending is the **formal mapping** — and, more than for the other derivations, a set
of **inherited open problems** that the mapping does not resolve.

**Where the epoch lives.** The natural temptation is to call the universal wavefunction *the*
epoch — but its unitary evolution never ends and never fails an invariant, so that reading is
trivial (an eternal epoch whose ψ = "unitarity holds" adds no formal power; cf. `README.md` §3).
The load-bearing reading puts the epoch at the **branch**: a *world* is an epoch, born at a
decoherence event and bounded by the persistence of its decohered, quasi-classical identity. The
universal wavefunction is then **Epoch 0**, the superstate that contains them all.

## Relationship to the Epoch Automaton

The Universal-Wavefunction Epoch instantiates the Epoch Automaton `E = (S, Σ, δ, s₀, F, ψ)` over
Hilbert space:

| Component | embraOS (Digital Ark) | MWA (Many-Worlds / Everett) |
|---|---|---|
| **States S** | Session states | Wavefunctions — points in Hilbert space ℋ |
| **Alphabet Σ** | Input tokens, API calls | Interactions / measurements — system–environment couplings |
| **Transition δ** | Request routing, tool dispatch | The unitary Schrödinger flow U(t) = e^{−iĤt/ℏ} |
| **Initial s₀** | First sealed **soul** document | Genesis universal wavefunction Ψ₀ |
| **Accepting F** | Valid session continuation | Einselected, quasi-classical (pointer-basis) worlds F_ℋ |
| **Invariant ψ** | **soul** document verification | Decoherent quasi-classical identity of a branch |

**The crucial difference.** In embraOS, ψ is an external check at each boot. In QNM it is a
*projection* (`P_ψ`); in SOL a *conservation law* (`Γ_ψ` is flow-invariant). In MWA it is neither
— the global flow `U` enforces no boundary on the universal wavefunction, because a projection
would be wavefunction *collapse*, which Everett's interpretation exists to deny. Instead the
boundary is **emergent**: decoherence (einselection) continually selects a quasi-classical pointer
basis, and a *branch* persists exactly as long as it stays decohered from its siblings. The
boundary is not checked, not projected, not conserved — it is **selected by the environment**.

## Boundary-Native Architecture

Conventional safety operates as *filtering*: generate, then check. The Epoch framework instead
seals the boundary into the system; QNM seals it into geometry, SOL into a conservation law. MWA
seals it into **the structure of entanglement**. This draws directly from the Epoch definition:

> *An epoch is a bounded interval defined not by duration but by the persistence of a coherent
> boundary condition.*

In MWA, the boundary condition is what a *world* is. A branch's epoch persists because, once it has
decohered, the off-diagonal terms that would let it re-interfere with its siblings are dispersed
into an astronomically large environment. Leaving the branch — **recoherence** — is not a step the
unitary flow takes from inside a world; it would require reassembling that dispersed phase
information, which *ends the epoch* (re-merges the world) rather than continuing it, and is
overwhelmingly suppressed in practice.

### Candidate Mechanisms

1. **Environment-induced superselection (einselection).** Decoherence singles out a preferred
   *pointer basis* — the states robust under monitoring by the environment (Zurek). The pointer
   states *are* the worlds; the selection is dynamical, not imposed. This is the MWA analogue of
   QNM's `P_ψ` and SOL's conserved `E < 0`: the mechanism that keeps the system "on" its invariant.

2. **Reduced-density-matrix diagonalization.** Tracing out the environment,
   `ρ_S = Tr_E |Ψ⟩⟨Ψ|`, the off-diagonal (interference) terms decay toward zero in the pointer
   basis. The vanishing of coherence between branches is the precise sense in which "a world keeps
   its identity."

3. **Approximate irreversibility (the FAPP arrow).** Decoherence is *for all practical purposes*
   irreversible, not strictly so — exactly as the KAM/Laskar precedent makes SOL's binding only
   *approximately* conserved. This is a feature, not a caveat to hide: it is precisely because a
   branch's identity is only approximately permanent that the epoch **can** end (by recoherence).

4. **Retrocausal handshake (speculative).** A bidirectional variant `δ*: S × S × Σ → [0,1]`, as in
   QNM's and SOL's Candidate Mechanisms. It is **deliberately absent** from the state-machine
   below; the Schrödinger flow is forward-directed, and the retrocausal reading is a motivating
   metaphor (`README.md` §4), not part of the formulation.

## Connection to Decoherence Theory and the Everett Interpretation

Where QNM points to the USTC nine-spin quantum reservoir and SOL to celestial mechanics and the
KAM theorem, MWA points to the Everett interpretation itself and to the theory of environmental
decoherence:

- **The relative-state formulation** (Everett, 1957). Quantum mechanics with the collapse
  postulate removed: the universal wavefunction evolves unitarily, and observers' records are
  defined only *relative to* a branch. This is the rigorous statement that there is no external
  observer — the basis for reading the Ark as branch-internal.

- **Environmental decoherence** (Joos & Zeh, 1985). Interaction with an environment locally
  destroys phase relations between pointer states; the surviving coherence determines the
  "classical" properties of macroscopic systems. This is the mechanism by which branches become,
  and stay, distinct.

- **Einselection and pointer states** (Zurek, 2003). The environment monitors certain observables
  and "einselects" the basis in which the reduced density matrix is diagonal — the preferred basis
  the branches are written in.

These ground "ψ as a persistent invariant" the way KAM grounds SOL's: decoherence makes
branch-identity *robust*, not merely initially true. They do **not**, however, settle why the
branch weights should be the *probabilities* — see the open problems below.

## Formal Definition: The MWA Automaton

Extending the Epoch Automaton 6-tuple over Hilbert space, with a complex (unitary) flow:

```
MWA = (ℋ, Ĥ, U, Ψ₀, F_ℋ, ψ)
```

Where:

| Symbol | Meaning |
|---|---|
| **ℋ** | Hilbert space — the continuous (complex) state space; each Ψ ∈ ℋ is a wavefunction |
| **Ĥ** | The Hamiltonian *operator* (self-adjoint); generates the flow. Hatted — an operator, not QNM/SOL's scalar `H` |
| **U** | The unitary Schrödinger flow U(t) = e^{−iĤt/ℏ}, generated by iℏ ∂Ψ/∂t = ĤΨ; **complex** and **norm-preserving** |
| **Ψ₀** | Initial universal wavefunction, ψ(Ψ₀) = true |
| **F_ℋ** ⊆ ℋ | Einselected, quasi-classical (pointer-basis) configurations — the coherent worlds |
| **ψ: ℋ → {true, false}** | **soul** invariant — at the superstate, unitarity (⟨Ψ\|Ψ⟩ = 1); at a branch, decoherent quasi-classical identity |

with the branch machinery: `ℋ = ℋ_S ⊗ ℋ_E` (a system–environment split), `ρ_S = Tr_E |Ψ⟩⟨Ψ|`
(reduced density matrix), `|c_k|²` (the Born weight of branch *k*), and `ψ_sub^k` / `δ_sub^k`
(each world's sub-invariant / sub-transition).

**Key property (boundary-native via decoherence):**

Unitary U preserves ⟨Ψ|Ψ⟩ = 1 globally — the superstate invariant never fails. Within Ψ,
einselection makes the pointer-basis branches quasi-classical, and each branch *k* persists while
the off-diagonal terms of ρ_S coupling it to its siblings stay ≈ 0:

∀ branch k decohered from its siblings: ψ_sub^k(branch) = true

The universal wavefunction cannot "leave" an invariant region — there is none to leave, because
the flow is globally unitary. A *branch* ends not by the flow exiting a region but by
**recoherence**, which is astronomically suppressed but never forbidden. The boundary is
**environment-selected**, not checked, projected, or conserved.

### The MWA State-Machine

The same state-machine, expressed for the branching wavefunction. Where the discrete Epoch
Automaton checks ψ at every crossing, QNM builds ψ into geometry via a projection, and SOL
conserves ψ, the MWA Automaton lets ψ **emerge**: the unitary flow `U` never collapses or rejects,
and einselection picks out the pointer-basis worlds, each of which persists while it stays
decohered from its siblings. It is forward-directed, exactly as the core state-machine is.

```
                 ┌───────────────────────────────────────────────┐
                 │    THE ARK · the universal wavefunction Ψ     │
                 │      + Schrödinger dynamics  iℏ ∂ₜΨ = ĤΨ      │
                 │   CORRESPONDENCE, not mechanism: MWI has no   │
                 │   "outside"; U never rejects (cf. README §4)  │
                 └───────────────────────┬───────────────────────┘
                                         │ ψ = unitarity (⟨Ψ|Ψ⟩=1, conserved by U) — not checked; einselection picks the pointer basis
                                         ▼
   ┌──────────────────────────────────────────────────────────────────────────┐
   │  HILBERT SPACE  ℋ      (state space; generator Ĥ; complex flow U)        │
   │                                                                          │
   │  EPOCH 0 · Ψ  (superstate)   genesis Ψ₀,  ψ₀ = unitarity (always holds)  │
   │                                                                          │
   │     Ψ ──U──▶ decoheres ──┬──▶ world 1 · |c_1|² · ψ_sub^1 ──▶ [ F_ℋ ]     │
   │     (the branching fork) ├──▶ world 2 · |c_2|² · ψ_sub^2 ──▶ [ F_ℋ ]     │
   │                          └──▶ world 3 · |c_3|² · ψ_sub^3 ──▶ [ F_ℋ ]     │
   │                                                                          │
   │  F_ℋ = einselected, quasi-classical (pointer-basis) worlds.              │
   │  Each world k persists while ρ_S off-diagonals to siblings ≈ 0.          │
   │  · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · │
   │  ψ = false analogue — RECOHERENCE: a world re-interferes with a sibling. │
   │  Astronomically rare, never forbidden (decoherence only ~irreversible).  │
   └──────────────────────────────────────────────────────────────────────────┘
                                         │ the branching tree IS the record (relative state)
                                         ▼
   ┌──────────────────────────────────────────────────────────────────────────┐
   │  MEMORY / RECORD  M   —   a FORKING TREE, not a single list              │
   │                                                                          │
   │     Ψ₀ ─▶ Ψ₁ ─┬─▶ world 1 : its own relative-state record                │
   │               ├─▶ world 2 : its own relative-state record                │
   │               └─▶ world 3 : …     records are branch-relative (Everett)  │
   └──────────────────────────────────────────────────────────────────────────┘
                                         ▲
                                         │ queries (read-only)
                                 ┌───────┴────────────────────┐
                                 │ THE STEWARD                │
                                 │ the in-branch observer.    │
                                 │ CAVEAT: itself inside Ψ —  │
                                 │ it branches too, so the    │
                                 │ external  ∉ ℋ  is strained │
                                 └────────────────────────────┘
```

The discrete machine's verification step — the Ark's σ_verify, the hero figure's `ψ?` gate — has
**no clean analogue here**: unitary evolution never rejects a transition (that would be collapse).
The nearest thing is **einselection**, which does not forbid branches but *selects* which ones are
robust enough to count as worlds.

**Discrete state-machine ↔ MWA, element by element:**

| Discrete Epoch Automaton `E` | MWA Automaton | Note |
|---|---|---|
| state `s ∈ S` | wavefunction `Ψ ∈ ℋ` | a discrete node becomes a point in Hilbert space |
| transition `δ(sᵢ, σⱼ)` | a step of the unitary flow `U` | complex, norm-preserving; iℏ ∂ₜΨ = ĤΨ |
| verification step (`σ_verify`) | einselection (no rejection) | U never rejects; the environment *selects* the pointer basis |
| halt when `ψ(s) = false` | recoherence of a branch (astronomically rare) | leaving a world by re-interference; never forbidden |
| initial epoch `s₀` | initial wavefunction `Ψ₀`, `ψ(Ψ₀) = true` | the genesis configuration |
| terminal set `F ⊆ S` | quasi-classical set `F_ℋ ⊆ ℋ` | einselected, pointer-basis worlds |
| nested epoch `(S_sub, …, ψ_sub)` | a branch, with `δ_sub^k`, `ψ_sub^k` | Ψ = Epoch 0 superstate; worlds = sub-epochs (illustrative — not formalized; see below) |
| Memory `M = [(s₀,σ₁,s₁), …]` | a **forking tree** of branch-relative records | the run is no longer a single list — it splits (Everett relative state) |
| Steward (oracle, `∉ S`) | in-branch observer (`∉ ℋ` strained) | there is no outside — see the open problems |

> Note — `ψ` here is still **pointwise** (`ψ: ℋ → {true, false}`), the continuous analogue of the
> *static* discrete invariant. It does **not** by itself resolve the dynamic / trajectory-dependent
> ψ flagged as the open formal problem (`README.md` §6). But decoherence is *inherently
> history-dependent* — whether a branch is "the same world" depends on the decoherence record laid
> down along its trajectory — so MWA is the most natural setting in the project to *attempt* a
> trajectory-valued ψ. That attempt is open work, **not** done here.

**Operational reading** (the branching counterpart of the legend's composite expressions):

```
Initialise    start at Ψ₀ with ψ(Ψ₀) = true        (genesis universal wavefunction)
Step          Ψ → Ψ'  via  U(t) = e^{−iĤt/ℏ}       (unitary; iℏ ∂ₜΨ = ĤΨ; norm-preserving)
Branch        at a decoherence event Ψ splits → worlds {k}, weights |c_k|², each ψ_sub^k = true
Accept        a quasi-classical (pointer-basis) world with Ψ ∈ F_ℋ
End-of-world  recoherence: ρ_S off-diagonals to a sibling revive (astronomically rare)
```

**Nesting — the universal wavefunction as Epoch 0, the worlds as sub-epochs.** Ψ is the superstate
(Epoch 0, `s₀`/`Ψ₀`): while it evolves unitarily, the worlds branch within it. Each world *k* is a
nested sub-automaton with its own invariant `ψ_sub^k` (it keeps its decoherent, quasi-classical
identity) and its own sub-transition `δ_sub^k`. Per the legend's §8 nesting constraint, while the
outer invariant holds the sub-invariants are evaluated independently:

```
ψ(Ψ) = true  ⇒  ∀ world k,  ψ_sub^k is evaluated independently
```

This is a concrete **illustration** of the statechart nesting sketched in `README.md` §3 — and it
presses on that open problem *harder* than SOL does. A Harel superstate persists *alongside* its
unchanged substates; here the parent branch does **not** persist beside its children — its Born
weight is **partitioned among them** (the `|c_k|²` sum to the parent's weight). Measure-partitioning
branching is not a standard statechart move, so MWA gives a vivid instance of the open nesting
problem (`README.md` §6) — **not** a resolution of it.

**The Steward, in MWA terms** — and here the framework genuinely strains. In the core machine the
Steward is an external oracle (`Steward ∉ S`); QNM and SOL preserve this (`∉ M`, `∉ Γ`). MWI does
not allow it: every observer is a subsystem of Ψ and branches along with it.

```
Steward ∉ ℋ                            (strained: MWI has no "outside")
Steward may query:   its own branch's relative-state record,  ψ
Steward may not:     drive U  (the unitary flow)
```

The honest reading is that the Steward becomes the **in-branch observer**: it still does not drive
the flow, but it is no longer external — it sits inside a world and forks when that world does.
There is no global Steward, only branch-relative ones. The same pressure applies to the Ark; see
the correspondences and open problems below.

*Mapping only. The quantum system itself is operational by nature; what this figure illustrates is
the **Formal mapping (drafted)** row of the Current Status table below — the correspondence between
the Epoch Automaton and unitary quantum dynamics with decoherence. It is forward-directed by
design; the speculative retrocausal variant `δ*` is deliberately not part of it. The Born-rule,
preferred-basis, and no-outside problems below are **inherited and unresolved**.*

## Motivating Correspondences (NOT physical mechanism)

The following make the structure vivid. **None is claimed as a mechanism, a derivation, or a
statement about physical reality.** They are worked illustrations of metaphors already fenced in
`README.md` §4 — and here, unusually, the fencing is *forced* by the interpretation: MWI has no
outside, so the Ark and Steward cannot literally be external.

**The universal wavefunction Ψ ↔ the Ark.**
- *Inspired:* Ψ together with the Schrödinger dynamics is the one object that "contains" every
  branch and every record — a definition-plus-memory of the whole, as the Ark is the system's
  definition plus its memory. It is also no single world, echoing "the Ark is not a state in the
  system."
- *Not claimed:* that Ψ *observes, defines, or verifies* anything. Unitary evolution never rejects
  a transition; there is no σ_verify. The nearest dynamical analogue, einselection, *selects* a
  basis but forbids nothing.

**The relative-state record ↔ Memory (M).**
- *Inspired:* Everett's relative states are exactly a record kept *relative to* a branch — a memory
  that forks with the worlds.
- *Not claimed:* that there is a single global log. There is not — the record is a tree of
  branch-relative records, with no observer able to read across branches.

**The in-branch observer ↔ the Steward.**
- *Inspired:* an agent who reads the record and tends the boundary — Wheeler's participatory stance
  (`README.md` §4).
- *Not claimed:* an *external* Steward. The observer is inside Ψ and branches with it; the external
  `∉ ℋ` of the core framework cannot hold. This is the sharpest way MWI strains the architecture.

These correspondences are decoration — and, here, a diagnosis. The automaton
`MWA = (ℋ, Ĥ, U, Ψ₀, F_ℋ, ψ)` stands on standard quantum mechanics with or without them; what the
correspondences reveal is precisely *where* the framework's external-observer assumptions break.

## Open problems (inherited, not resolved)

MWA inherits hard problems from both the Many-Worlds interpretation and the core framework. None is
solved here; each is flagged in the spirit of `README.md` §6.

- **The Born rule.** Reading `|c_k|²` as the *measure* (probability / weight) on worlds invokes the
  single most contested piece of MWI — why a deterministic, unitary theory should yield Born-rule
  probabilities at all. Decision-theoretic derivations exist (Deutsch; Wallace, 2012) and remain
  contested. MWA *uses* the Born weights; it does not derive them.

- **The preferred-basis / factorization problem.** Decoherence requires a system–environment split
  `ℋ = ℋ_S ⊗ ℋ_E`; which factorization is "right" is not fixed by the bare Hilbert space. The
  pointer basis — and hence what counts as a "world" — depends on that choice.

- **No "outside" for the Ark or Steward.** The core framework requires the Ark and Steward to sit
  external to the automaton (`∉ S`). MWI forbids it. Two readings, neither asserted as a
  resolution: (a) **Ark = Ψ + Schrödinger dynamics** — preserves "not a single state," but then
  nothing ever *verifies* (U never rejects); (b) **Ark = relative state** — records are
  branch-relative, but then the Ark is internal and branches too. The tension is genuine and is the
  most interesting thing MWA surfaces.

- **ψ is still pointwise.** A static branch-identity predicate adds no formal power; the
  trajectory-dependent ψ that *would* (`README.md` §6, "the main formal lever") is exactly what
  decoherence's history-dependence invites but does not, here, supply.

## Current Status

| Phase | Status |
|---|---|
| **Theoretical foundation** | ✅ Established — Epoch Automaton formalism (2026) |
| **Physical precedent** | ✅ Established — unitary QM; Everett relative-state formulation; environmental decoherence / einselection |
| **Formulation** | ✅ Drafted — MWA Automaton (this document) |
| **Born rule · preferred basis · no-outside Ark · dynamic ψ** | ⬜ Open — inherited from MWI and the core framework; not resolved here |

## References

- `README.md` — Formal Epoch definition and state-machine framework (and §4, the fenced motivating
  metaphors invoked above)
- `EPOCH-NOTATION-LEGEND.md` §11 — the MWA notation registered for this derivation
- Everett, H. (1957). "'Relative State' Formulation of Quantum Mechanics," *Reviews of Modern
  Physics* **29**(3), 454–462
- Joos, E. & Zeh, H. D. (1985). "The emergence of classical properties through interaction with the
  environment," *Zeitschrift für Physik B* **59**(2), 223–243
- Zurek, W. H. (2003). "Decoherence, einselection, and the quantum origins of the classical,"
  *Reviews of Modern Physics* **75**(3), 715–775
- Wallace, D. (2012). *The Emergent Multiverse: Quantum Theory according to the Everett
  Interpretation.* Oxford University Press (decision-theoretic Born-rule program — contested)
