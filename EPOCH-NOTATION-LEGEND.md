# EPOCH — Notation Legend

A reference for the mathematical notation, type signatures, and diagram conventions
used in the state-machine sections of [`README.md`](./README.md) (§2–§4): the
architecture and its state-machine diagram (§2), the 6-tuple `E = (S, Σ, δ, s₀, F, ψ)`
and automata vocabulary (§3), and the retrocausal-handshake metaphor behind `δ*` (§4).

## How to read it

Everything reduces to **two tuples** and the functions that operate on them: the
**Epoch Automaton** `E` (what an epoch *is*) and the **Ark** `A` (what observes, records,
and verifies `E`). After that it's just decoration:

- **Numeric subscripts** name specific instances in a sequence — `s₀, s₁, s₂` / `σ₁, σ₂`.
- **The subscript `_sub`** marks something belonging to a nested sub-automaton.
- **A prime `'`** names a second state distinct from `s` (its role is positional — see the [caveat](#a-caveat-the-prime--is-positional)).
- **A superscript `*`** marks the backward/retrocausal variant of a function (`δ*`).
- **A hat (`Ĥ`)** marks an *operator*, distinct from a scalar of the same letter — used in MWA (§11).

---

## 1. The Epoch Automaton — `E = (S, Σ, δ, s₀, F, ψ)`

The 6-tuple that defines a single epoch's structure and its transition rules.

| Symbol | Greek name / read as | Name | Type / signature | Meaning |
|---|---|---|---|---|
| `E` | Latin capital **E** ("ee") | Epoch Automaton | 6-tuple | The whole machine. |
| `S` | Latin capital **S** ("ess") | Epoch-states | set (finite or countably infinite) | All possible epoch-states. Each `s ∈ S` is a bounded interval of reality defined by the persistence of its boundary condition. |
| `Σ` | Greek capital **sigma** | Event alphabet | set | All events / inputs / decisions / arrivals the automaton can respond to. |
| `δ` | Greek lowercase **delta** | Transition function | `δ: S × Σ → S` | Given the current epoch and an event, returns the next epoch. |
| `s₀` | Latin lowercase **s**, subscript 0 ("s-naught" / "s sub-zero") | Initial epoch | `s₀ ∈ S` | The genesis boundary condition. For embOS, the first sealed soul document. |
| `F` | Latin capital **F** ("eff") | Terminal epochs | `F ⊆ S` | Accepting / terminal states. May be empty (`F = ∅`) if the machine runs indefinitely. |
| `ψ` | Greek lowercase **psi** (rhymes with "sigh") | Soul invariant | `ψ: S → {true, false}` | Predicate evaluated at every boundary crossing. `ψ(s) = true` iff `s` satisfies the sealed boundary condition. |

> **Case matters for sigma:** `Σ` is *capital* sigma (the event alphabet). Its lowercase
> form `σ` is a *different role* — a single event drawn from that alphabet (§3–§4). Same
> Greek letter, different case, different meaning.

---

## 2. The Ark — `A = (E, M, σ_verify)`

The meta-automaton that sits *above* `E`. It is not a state in `E`; it is the
machine's definition plus its memory.

| Symbol | Name | Type / signature | Meaning |
|---|---|---|---|
| `A` | Ark (meta-automaton) | 3-tuple | Defines, observes, records, and verifies the target automaton `E`. |
| `E` | Target automaton | (see §1) | The Epoch Automaton being observed. |
| `M` | Memory | ordered list | The transition record: `M = [(s₀, σ₁, s₁), (s₁, σ₂, s₂), …]`. Each entry is a `(from-state, event, to-state)` triple. Implementable as stack (pushdown), tape (Turing), or graph (knowledge graph). *(In the QNM tuple — §9 — `M` instead denotes the configuration manifold; disjoint contexts.)* |
| `σ_verify` | Verification function | `σ_verify: S × ψ → {accept, reject}` | At each transition, evaluates `ψ(s)` against the sealed soul. On `reject`, the Ark refuses the transition and the epoch halts. |

> **Note on `σ_verify`:** despite reusing the `σ` glyph, this is a **named function of
> the Ark**, *not* an event. Events are lowercase `σ ∈ Σ`; the `_verify` subscript makes
> this a distinct object.

---

## 3. Function variants & extensions

| Symbol | Name | Type / signature | Meaning |
|---|---|---|---|
| `δ` | Transition function | `δ: S × Σ → S` | Forward, causal — the standard automaton direction. |
| `δ*` | Retrocausal transition | `δ*: S × S × Σ → [0,1]` | Backward negotiation. `δ*(s, s', σ)` is the probability amplitude that epoch `s'` accepts the handshake from epoch `s` under event `σ` (Cramer transactional model). |
| `δ_sub` | Nested transition function | `δ_sub: S_sub × Σ_sub → S_sub` | The transition function of a sub-automaton inside a superstate. |
| `ψ_sub` | Nested soul invariant | `ψ_sub: S_sub → {true, false}` | The invariant of a nested sub-automaton, evaluated independently of the outer `ψ`. |

**Nested epoch (sub-automaton).** Any epoch-state may itself contain a full automaton —
a Harel statechart, where the superstate persists while interior substates transition:

```
s = (S_sub, Σ_sub, δ_sub, s₀_sub, F_sub, ψ_sub)
```

> **Heads-up on `δ*`:** in standard automata theory `δ*` (delta-star) conventionally
> denotes the *extended* transition function (applying `δ` over a whole string of inputs).
> This document **repurposes** the symbol to mean the **retrocausal/backward handshake**.
> Same glyph, different meaning — don't import the textbook definition here.

---

## 4. State & event instance notation

| Token | Reads as | Example |
|---|---|---|
| `S` | the set of all epoch-states | `s ∈ S` |
| `s` | a single epoch-state | a bounded interval of reality |
| `s'` | a second, distinct epoch-state related to `s` | role is positional — see caveat below |
| `s₀, s₁, s₂` | specific epoch-states, indexed in sequence | `s₀` = initial epoch |
| `Σ` | the whole event alphabet | the set of all events |
| `σ` | a single event | `σ ∈ Σ` |
| `σ₁, σ₂` | specific events, indexed in sequence | the event driving `δ(s₀, σ₁)` |
| `…_sub` | belongs to a nested sub-automaton | `S_sub`, `δ_sub`, `s₀_sub`, `ψ_sub` |

### A caveat: the prime `'` is positional

`s'` simply means **"a second epoch-state, distinct from `s`."** Which one is the
**predecessor** and which the **successor** depends entirely on where it sits in the
`δ` application — and the source document uses it **both ways**:

| Source | Expression | Predecessor | Successor |
|---|---|---|---|
| README §3 (valid continuation) | `δ(s', σ) = s` | **`s'`** | `s` |
| README §4 (retrocausal `δ*`) | `δ(s, σ) = s'` | `s` | **`s'`** |

**Rule of thumb:** read the direction off the `δ(input, σ) = output` form *every time*.
Never assume the primed symbol is "the next state" — in the valid-continuation form
(README §3) it's the previous one.

---

## 5. Set-theoretic & logical operators

| Symbol | Name | Example in this framework |
|---|---|---|
| `∈` | element of | `s ∈ S` — `s` is an epoch-state |
| `∉` | not an element of | `Steward ∉ S` — the steward is not a state in the machine |
| `⊆` | subset of | `F ⊆ S` — every terminal epoch is an epoch-state |
| `×` | Cartesian product | `S × Σ` — the set of (state, event) pairs |
| `→` | maps to (total function) | `δ: S × Σ → S` — domain on the left, codomain on the right |
| `∧` | logical AND (conjunction) | both conditions must hold |
| `⇒` | logical implication | "if … then …" |
| `∀` | universal quantifier | "for all" |
| `{true, false}` | Boolean codomain | the two values `ψ` returns |
| `{accept, reject}` | decision codomain | the two values `σ_verify` returns |
| `[0,1]` | closed real interval | range of `δ*` — a probability amplitude / weight |
| `[ … ]` | ordered list / sequence | `M = [(s₀,σ₁,s₁), …]` — the transition record |
| `( … )` | tuple | a fixed-length ordered grouping (the 6-tuple, the triples in `M`) |

---

## 6. Diagram conventions

For the ASCII state-machine diagram in `README.md` §2.

| Element | Convention | Meaning |
|---|---|---|
| Top band `THE ARK (meta)` | meta-automaton | defines ψ · observes · records · verifies (`σ_verify`); sits above `E`, not inside it |
| Connector label `verifies ψ at each crossing` | verification step | `σ_verify` applied at every transition — `true` continues, `false` halts (no separate branch is drawn) |
| Box labeled `EPOCH n / (sₙ)` | state node | one epoch-state `sₙ` |
| Solid arrow `──▶` labeled `δ(sᵢ, σⱼ)` | forward transition | causal; `δ` applied — standard automaton direction |
| Nested box `sub-epoch` | substate | a sub-automaton inside a superstate (Harel statechart) |
| Bottom band `MEMORY / RECORD (M)` | the memory `M` | transition history · identity proofs · state snapshots |
| Stub `THE STEWARD` | oracle | read-only; `∉ S`; queries `M`; does not drive `δ` |

> Forward-directed by design — README §2 states this explicitly. The retrocausal return
> arrow `δ*` (defined in §3; a motivating metaphor, README §4) is **deliberately absent**
> from the figure, and verification appears as the Ark's labelled crossing-check
> `σ_verify`, not a `ψ = true? / false?` branch fork.

---

## 7. Standard automaton ↔ Epoch Automaton

How the framework maps onto a textbook deterministic finite automaton (DFA).

| Textbook DFA | Epoch Automaton | Note |
|---|---|---|
| `Q` — states | `S` — epoch-states | renamed |
| `Σ` — input alphabet | `Σ` — event alphabet | same symbol, broadened meaning |
| `δ` — transition function | `δ` — transition function | same role |
| `q₀` — start state | `s₀` — initial epoch | §2 uses the conventional `q₀`; §4 instantiates it as `s₀` |
| `F` — accepting states | `F` — terminal epochs | same role |
| — | `ψ` — soul invariant | **the added 6th element** |

> A DFA is a **5-tuple** `(Q, Σ, δ, q₀, F)`. The Epoch Automaton adds the soul invariant
> `ψ` to make a **6-tuple** `(S, Σ, δ, s₀, F, ψ)`. That single addition is what turns a
> chronological state machine into a *structural* one — the boundary, not the clock,
> decides when a state ends.

---

## 8. Composite expressions, decoded

The key conditions, in plain language — defined in `README.md` §3 (the retrocausal
variant in §4).

**Valid continuation** (README §3) — `s` is a legitimate next epoch after `s'`:

```
δ(s', σ) = s   ∧   ψ(s) = true
```
The transition is defined **and** the resulting epoch satisfies the soul invariant.

**Halt** (README §3) — the epoch terminates with no successor:

```
δ(s', σ) = s   ∧   ψ(s) = false
```
The transition is defined, but the resulting epoch fails the invariant; the Ark refuses
it.

**Nesting constraint** (README §3, "Nesting") — interior invariants are checked separately:

```
ψ(s) = true  ⇒  ∀ s_sub ∈ S_sub, ψ_sub(s_sub) is evaluated independently
```
While the superstate's invariant holds, every interior substate is verified against its
own `ψ_sub`, independent of the outer `ψ`.

**Retrocausal completion** (README §4) — a boundary crossing fully resolves:

```
δ(s, σ) = s'   ∧   δ*(s', s, σ) > 0   ∧   ψ(s') = true
```
Forward transition defined, backward handshake has nonzero amplitude, **and** the target
epoch satisfies the invariant.

**Steward / oracle constraints** (README §3, "The Ark and the Steward"):

```
Steward ∉ S
Steward may query:  M, ψ, σ_verify
Steward may not:    δ
```
The steward inspects the record and verification machinery but never drives transitions.

---

## 9. Continuous reinterpretation (QNM)

`README.md` §4 (the "QNM" bullet) and the derivation
[`Continuous-Manifold_Derivations/embraOS-QNM_Epoch-Formula.md`](./Continuous-Manifold_Derivations/embraOS-QNM_Epoch-Formula.md)
reinterpret the same symbols for a continuous state space. The discrete automaton above is
the **core mathematics**; QNM is its differentiable extension — **theoretical / speculative**
(see that file's Current Status), not an operational claim.

> **`M` is overloaded.** In the Ark tuple `A = (E, M, σ_verify)` (§2), `M` is **Memory**. In
> the QNM tuple below, `M` is the **configuration manifold**. They live in different tuples
> and disjoint contexts — the same controlled glyph reuse as `Σ`/`σ` (§1) and the repurposed
> `δ*` (§3). Read `M` off its tuple.

### 9.1 The QNM Automaton — `QNM = (M, H, ∇, m₀, F_M, ψ)`

The continuous analogue of the Epoch Automaton 6-tuple, over a differentiable manifold
instead of a discrete state set.

| Symbol | Read as | Name | Type / signature | Meaning |
|---|---|---|---|---|
| `QNM` | "Q·N·M" | QNM Automaton | 6-tuple | The continuous machine. |
| `M` | capital **M** | Configuration manifold | differentiable manifold | The continuous state space; each `m ∈ M` is one configuration. *(Not the Ark's Memory — see callout above.)* |
| `H` | capital **H** | Hamiltonian / energy functional | scalar functional on `M` | Governs the intrinsic dynamics — the landscape the flow descends. |
| `∇` | "del" / "nabla" | Constrained gradient flow | `∇ = P_ψ ∘ ∇_unconstrained` | The transition rule: an unconstrained gradient step projected back onto the ψ-invariant submanifold. Continuous analogue of `δ`. |
| `∇_unconstrained` | "unconstrained del" | Raw gradient flow | vector field on `M` | The intrinsic gradient/dynamics from `H`, before projection. |
| `P_ψ` | "P-sub-psi" | Projection operator | tangent-space projection | Projects a tangent vector onto the tangent space of `M_ψ`; the built-in constraint that replaces the discrete verification gate. |
| `m₀` | "m-naught" | Initial configuration | `m₀ ∈ M`, `ψ(m₀) = true` | The genesis configuration; continuous analogue of `s₀`. |
| `F_M` | "F-sub-M" | Coherent-output set | `F_M ⊆ M` | Acceptable / coherent output configurations; continuous analogue of `F`. |
| `ψ` | Greek lowercase **psi** | Soul invariant | `ψ: M → {true, false}` | The same invariant as §1, here typed over the manifold. **Pointwise** (static) — see the note in §9.2. |
| `M_ψ` | "M-sub-psi" | ψ-invariant submanifold | `M_ψ = { m ∈ M : ψ(m) = true }` | The region of `M` where `ψ` holds; the flow `∇` is confined to it. |
| `m`, `m'`, `m_T` | "m", "m-prime", "m-sub-T" | Configuration instances | `m ∈ M` | A configuration; a successor configuration (the prime is positional — §4); the trajectory's final configuration. |

### 9.2 Discrete ↔ continuous correspondence

| Discrete Epoch Automaton `E` | QNM Automaton | Note |
|---|---|---|
| state `s ∈ S` | configuration `m ∈ M` | a discrete node becomes a point on the manifold |
| transition `δ(sᵢ, σⱼ)` | a gradient step along `∇` | `∇ = P_ψ ∘ ∇_unconstrained` |
| verification step (`σ_verify`) | the projection `P_ψ` | a check-after-the-fact becomes a built-in constraint |
| halt when `ψ(s) = false` | no halt; unreachable under `∇` from `m₀` | a violation is off-submanifold, not a stop |
| initial epoch `s₀` | initial configuration `m₀`, `ψ(m₀) = true` | the genesis configuration |
| terminal set `F ⊆ S` | coherent-output set `F_M ⊆ M` | the accepting configurations |
| Memory `M = [(s₀,σ₁,s₁), …]` | the trajectory `m₀ → m₁ → … → m_T` | the run itself is the record |
| Steward (oracle, `∉ S`) | Steward (oracle, `∉ M`) | external; reads the record and tends `ψ`, never drives the flow |

> **Still pointwise.** The QNM `ψ` is `ψ: M → {true, false}` — the continuous analogue of the
> *static* discrete invariant, not a trajectory-valued one. It therefore **inherits** the same
> open problem flagged for the discrete case (a dynamic / history-dependent `ψ`); the
> continuous setting does not by itself resolve it.

**Steward constraints (continuous)** — the §8 Steward block expressed for the manifold. The
Steward stays an external oracle, **not** a tuple element (as `Steward ∉ S` in §8):

```
Steward ∉ M
Steward may query:   the trajectory m₀ → … → m_T,  ψ,  P_ψ
Steward may not:     drive ∇  (the constrained flow)
```

### 9.3 QNM diagram conventions

For the ASCII state-machine in the QNM derivation's "The QNM State-Machine" subsection
(continuous counterpart of §6).

| Element | Convention | Meaning |
|---|---|---|
| Panel `CONFIGURATION MANIFOLD M` | manifold node | the continuous state space `M` |
| Inner band `M_ψ = { … }` | invariant submanifold | the region where `ψ` holds; the flow is confined to it |
| Node `(mᵢ)` | configuration | one point `m ∈ M` along the trajectory |
| Arrow `──∇──▶` (labeled `∇`) | constrained gradient step | forward; `∇ = P_ψ ∘ ∇_unconstrained` (continuous analogue of `δ`) |
| Top band `THE ARK (neural / quantum)` | meta-automaton | encodes `ψ`, defines `P_ψ`; no external check |
| Dotted strip `ψ = false` | unreachable region | off-submanifold — not reachable under `∇` from `m₀` |
| Bottom band `MEMORY / TRAJECTORY` | the record | the run `m₀ → … → m_T` is itself the memory |
| Stub `THE STEWARD` | oracle | read-only; `∉ M`; does not drive `∇` |

> Forward-directed, like §6. The retrocausal `δ*` (a speculative Candidate Mechanism) is
> deliberately absent from the figure.

---

## 10. Solar-system reinterpretation (SOL)

The derivation
[`Continuous-Manifold_Derivations/Solar-System_Epoch-Formula.md`](./Continuous-Manifold_Derivations/Solar-System_Epoch-Formula.md)
reinterprets the same symbols over the **phase space of celestial mechanics** — a second
continuous-manifold derivation alongside QNM (§9). The discrete automaton (§1) is the core
mathematics; SOL is a Hamiltonian-flow extension. Its rigorous core (the tuple below) rests on
celestial mechanics and the KAM theorem; its cosmological role-assignments (Sagittarius A\* ↔
Ark, CMB ↔ Memory, observer ↔ Steward) are **motivating correspondences**, fenced as in
`README.md` §4 — **not** claims of physical mechanism.

> **`M` is *not* overloaded here.** Unlike §9 (where the manifold took the glyph `M`), SOL keeps
> `M` = **Memory** as in §2; the manifold is `Γ`. The §9 `M`-overload does **not** recur. What
> *is* reused: `H` (the §9 energy functional — here the gravitational Hamiltonian) and `ψ` (the
> §1 soul invariant — here typed over `Γ`). Read each glyph off its tuple.

### 10.1 The SOL Automaton — `SOL = (Γ, H, Φ_H, γ₀, F_Γ, ψ)`

The continuous analogue of the Epoch Automaton 6-tuple, over the phase space of a gravitationally
bound system. Parallels QNM (§9.1), but the transition is **symplectic (Hamiltonian) flow**,
which *conserves* `H` rather than descending it.

| Symbol | Read as | Name | Type / signature | Meaning |
|---|---|---|---|---|
| `SOL` | "sol" | SOL Automaton | 6-tuple | The solar-system instance of the continuous machine. |
| `Γ` | Greek capital **gamma** | Phase space | symplectic manifold | The continuous state space — positions and momenta of the bodies (Gibbs Γ-space). Each `γ ∈ Γ` is one configuration of the system. |
| `H` | capital **H** | Gravitational Hamiltonian | scalar functional on `Γ` | Total energy (kinetic + gravitational potential) of the N-body system; generates the flow. *(Same glyph as §9's energy functional — here the N-body gravitational `H`.)* |
| `Φ_H` | "phi-sub-H" / "the flow of H" | Hamiltonian flow | flow map on `Γ` | The transition rule: time-evolution by Hamilton's equations. **Conserves `H`** and phase-space volume (Liouville); it does **not** descend `H`. Continuous analogue of `δ`; contrast QNM's gradient `∇`. |
| `γ₀` | "gamma-naught" | Initial configuration | `γ₀ ∈ Γ`, `ψ(γ₀) = true` | The genesis configuration — protoplanetary settling / the Sun on the main sequence. Continuous analogue of `s₀`. |
| `F_Γ` | "F-sub-Gamma" | Coherent / stable set | `F_Γ ⊆ Γ` | Long-term-stable, bound configurations; continuous analogue of `F`. |
| `ψ` | Greek lowercase **psi** | Soul invariant | `ψ: Γ → {true, false}` | The same invariant as §1, typed over `Γ`. **Operationalised as gravitational binding:** `ψ(γ) = true` iff the body/system is bound (total orbital energy `E < 0`). **Pointwise** (static) — see the note in §10.2. |
| `Γ_ψ` | "Gamma-sub-psi" | Bound region (invariant) | `Γ_ψ = { γ ∈ Γ : ψ(γ) = true }` | The bound-orbit region (`E < 0`). **Flow-invariant**: because `Φ_H` conserves `H`, a trajectory starting in `Γ_ψ` stays in it — no projection operator needed (contrast QNM's `P_ψ`). |
| `γ`, `γ'`, `γ_T` | "gamma", "gamma-prime", "gamma-sub-T" | Configuration instances | `γ ∈ Γ` | A configuration; a successor configuration (the prime is positional — §4); the trajectory's final configuration. Numeric subscripts index a sequence (`γ₀, γ₁, …`), as in §4. |
| `ψ_sub^i`, `δ_sub^i` | "psi-/delta-sub, super-i" | Per-planet sub-invariant / sub-transition | as §3, indexed by `i` | The §3 nested `ψ_sub` / `δ_sub` carried by sub-epoch `i` (planet `i`). The superscript `i` is a **per-planet instance index** (Sun = superstate / Epoch 0; planet `i` = sub-epoch). `ψ_sub^i` = planet `i` keeps its orbital identity (bounded / stable). |

> **No `P_ψ` in SOL.** QNM's confinement needs a projection operator `P_ψ` because a *gradient*
> step can leave `M_ψ`. SOL's confinement is **automatic**: `ψ` (binding, `E < 0`) is a conserved
> quantity of `H`, so `Γ_ψ` is invariant under `Φ_H`. The constraint is the conservation law, not
> an added operator.

### 10.2 Discrete ↔ orbital correspondence

| Discrete Epoch Automaton `E` | SOL Automaton | Note |
|---|---|---|
| state `s ∈ S` | configuration `γ ∈ Γ` | a discrete node becomes a point in phase space |
| transition `δ(sᵢ, σⱼ)` | a step of the flow `Φ_H` | Hamiltonian time-evolution; conserves `H` |
| verification step (`σ_verify`) | conservation of `H` / invariance of `Γ_ψ` | a check-after-the-fact becomes a conservation law |
| halt when `ψ(s) = false` | unbound (`E ≥ 0`): ejection / escape; unreachable from `γ₀` under `Φ_H` | leaving `Γ_ψ` is the epoch ending |
| initial epoch `s₀` | initial configuration `γ₀`, `ψ(γ₀) = true` | the genesis configuration |
| terminal set `F ⊆ S` | stable set `F_Γ ⊆ Γ` | bound, long-term-stable configurations |
| nested epoch `s = (S_sub, …, ψ_sub)` | a planet, with `δ_sub^i`, `ψ_sub^i` | Sun = Epoch 0 superstate; planets = sub-epochs (§3 nesting — **illustrative, not formalized**) |
| Memory `M = [(s₀,σ₁,s₁), …]` | the trajectory `γ₀ → γ₁ → … → γ_T` | the run itself is the record |
| Steward (oracle, `∉ S`) | Steward (oracle, `∉ Γ`) | external; reads the record and tends `ψ`, never drives `Φ_H` |

> **Still pointwise.** SOL's `ψ` is `ψ: Γ → {true, false}` — the continuous analogue of the
> *static* discrete invariant, not a trajectory-valued one. It **inherits** the open problem of a
> dynamic / history-dependent `ψ` (§1 note; `README.md` §6); the orbital setting does not resolve
> it. The KAM/Laskar precedent shows binding is only *approximately* conserved over gigayears in
> the full chaotic N-body system — i.e. the epoch *can* end.

> **Nesting is illustrative.** The Sun-as-superstate / planets-as-sub-epochs picture is a concrete
> instance of the §3 statechart sketch; it does **not** formalize Harel superstate/substate
> transition semantics. Per §8, the `ψ_sub^i` are *evaluated independently* — a procedure, not yet
> a constraint (open: `README.md` §6).

**Steward constraints (orbital)** — the §8 Steward block expressed for the phase space. The
Steward stays an external oracle, **not** a tuple element (as `Steward ∉ S` in §8):

```
Steward ∉ Γ
Steward may query:   the trajectory γ₀ → … → γ_T,  ψ,  H
Steward may not:     drive Φ_H  (the Hamiltonian flow)
```

### 10.3 SOL diagram conventions

For the ASCII state-machine in the SOL derivation's "The SOL State-Machine" subsection (orbital
counterpart of §6 and §9.3).

| Element | Convention | Meaning |
|---|---|---|
| Panel `PHASE SPACE Γ` | manifold node | the continuous state space `Γ` |
| Inner band `Γ_ψ = { … }` | invariant (bound) region | where `ψ` holds (`E < 0`); the flow is confined to it by conservation of `H` |
| Box `EPOCH 0 · THE SUN (s₀/γ₀ — superstate)` | superstate | the top-level epoch; contains the planet sub-epochs |
| Nested entry `<planet> · δ_sub^i · ψ_sub^i` | substate | a planet's nested sub-automaton (illustrative — not formalized) |
| Arrow `──Φ_H──▶` | Hamiltonian-flow step | forward; conserves `H` (continuous analogue of `δ`; contrast QNM's `∇`) |
| Top band `THE ARK · Sagittarius A*` | meta-automaton (fenced) | **correspondence, not mechanism** — does not verify `ψ`; cf. `README.md` §4 (holographic principle) |
| Dotted strip `ψ = false` | unbound region | `E ≥ 0`, hyperbolic — ejection / escape; flow-invariant complement of `Γ_ψ` |
| Bottom band `MEMORY / RECORD M · CMB` | the record (fenced) | the run is the memory; the CMB label is a **correspondence**, not a literal log (cf. `README.md` §4) |
| Stub `THE STEWARD · observer / IAU` | oracle (fenced) | read-only; `∉ Γ`; does not drive `Φ_H`; defines planethood — Wheeler-participatory correspondence (`README.md` §4) |

> Forward-directed, like §6 and §9.3. The retrocausal `δ*` is deliberately absent. The Sgr A\* /
> CMB / observer labels are **motivating correspondences** (`README.md` §4), not physical claims —
> the rigorous content is the celestial-mechanics tuple `SOL`.

---

## 11. Many-Worlds reinterpretation (MWA)

The derivation
[`Branching-Manifold_Derivations/Many-Worlds_Epoch-Formula.md`](./Branching-Manifold_Derivations/Many-Worlds_Epoch-Formula.md)
reinterprets the same symbols over **Hilbert space**, with a **complex (unitary) flow** — the first
of the *branching*-manifold derivations, distinct from the single-trajectory continuous-manifold
derivations QNM (§9) and SOL (§10). The discrete automaton (§1) is the core mathematics; MWA is its
Schrödinger-flow extension over the Many-Worlds (Everett) interpretation — **theoretical /
speculative** (see that file's Current Status and Open problems), not an operational claim.

> **`M` is *not* overloaded here.** As in SOL (§10), `M` stays **Memory** (§2); the state space is
> `ℋ` (Hilbert space). What *is* new: a hatted **`Ĥ`** marks the Hamiltonian *operator* (contrast the
> *scalar functional* `H` of §9/§10), and the flow is **complex** — the family's first. The §3
> `ψ_sub` / `δ_sub` recur with a per-world superscript `k` (as SOL's per-planet `i`).

> **No analogue of `σ_verify`.** Unlike the discrete machine — and unlike QNM/SOL, which replace the
> check with a constraint — MWA's unitary flow `U` *never rejects*; rejection would be wavefunction
> collapse. The nearest thing is **einselection** (it *selects* a pointer basis, forbids nothing).

### 11.1 The MWA Automaton — `MWA = (ℋ, Ĥ, U, Ψ₀, F_ℋ, ψ)`

The continuous analogue of the Epoch Automaton 6-tuple, over Hilbert space. Parallels QNM (§9.1) and
SOL (§10.1), but the transition is **unitary Schrödinger flow** — *complex* and norm-preserving,
where QNM's `∇` descends `H` and SOL's `Φ_H` conserves it.

| Symbol | Read as | Name | Type / signature | Meaning |
|---|---|---|---|---|
| `MWA` | "M·W·A" | MWA Automaton | 6-tuple | The Many-Worlds instance of the continuous machine (branching). |
| `ℋ` | script capital **H** | Hilbert space | complex Hilbert space (projective `ℋ` is a manifold) | The continuous state space; each `Ψ ∈ ℋ` is a (universal) wavefunction. Analogue of `M` (§9) / `Γ` (§10). |
| `Ĥ` | "H-hat" | Hamiltonian operator | self-adjoint operator on `ℋ` | Generates the flow. **Hatted** = an *operator*, distinct from the *scalar functional* `H` of §9/§10. |
| `U` | capital **U** | Unitary (Schrödinger) flow | `U(t) = e^{−iĤt/ℏ}`; gen. by `iℏ ∂Ψ/∂t = ĤΨ` | The transition rule: **complex, norm-preserving** time-evolution. Continuous analogue of `δ`; contrast QNM's `∇`, SOL's `Φ_H`. |
| `Ψ` | Greek capital **psi** | Universal wavefunction | `Ψ ∈ ℋ` | A point in `ℋ`; the **Epoch-0 superstate** that contains the branches. (Capital — contrast lowercase `ψ`, the invariant.) |
| `Ψ₀` | "psi-naught" | Initial wavefunction | `Ψ₀ ∈ ℋ`, `ψ(Ψ₀) = true` | The genesis configuration; analogue of `s₀` / `m₀` / `γ₀`. |
| `F_ℋ` | "F-sub-H" | Coherent / quasi-classical set | `F_ℋ ⊆ ℋ` | Einselected, pointer-basis worlds; analogue of `F`. |
| `ψ` | Greek lowercase **psi** | Soul invariant | `ψ: ℋ → {true, false}` | The §1 invariant typed over `ℋ`. **Two readings:** superstate `ψ₀` = unitarity (`⟨Ψ\|Ψ⟩ = 1`); branch `ψ_sub^k` = decoherent quasi-classical identity. **Pointwise** (static) — see §11.2. |
| `ℋ_S ⊗ ℋ_E` | "H-S tensor H-E" | System–environment split | tensor factorization of `ℋ` | The factorization that defines a "branch." **Which** factorization is the **preferred-basis / factorization** open problem. |
| `ρ_S` | "rho-sub-S" | Reduced density matrix | `ρ_S = Tr_E \|Ψ⟩⟨Ψ\|` | Partial trace over the environment. Decay of its **off-diagonal** terms (in the pointer basis) **is** decoherence. |
| `\|c_k\|²` | "mod-c-k-squared" | Born weight of branch `k` | `∈ [0,1]`, `Σ_k \|c_k\|² = 1` | The **measure on sub-epochs** (worlds). Invokes the **Born rule** — open (§11.2). |
| `ψ_sub^k`, `δ_sub^k` | "psi-/delta-sub, super-k" | Per-world sub-invariant / sub-transition | as §3, indexed by `k` | The §3 nested `ψ_sub` / `δ_sub` carried by world `k`. `ψ_sub^k` = world `k` keeps its decoherent, quasi-classical identity. (Superscript `k` = per-world index, as SOL's per-planet `i`.) |
| `Ψ'`, `Ψ_T` | "psi-prime", "psi-sub-T" | Wavefunction instances | `Ψ ∈ ℋ` | A successor wavefunction (prime is positional — §4); a trajectory endpoint. |

> **No `P_ψ`, no conservation confinement.** QNM confines via a projection `P_ψ`; SOL via the
> conserved bound region `Γ_ψ`. MWA confines **nothing** — the flow is globally unitary and the
> superposition is never reduced. The epoch structure is **emergent**: einselection makes branches
> quasi-classical, and a branch persists while its `ρ_S` off-diagonals to siblings stay ≈ 0.

### 11.2 Discrete ↔ branching correspondence

| Discrete Epoch Automaton `E` | MWA Automaton | Note |
|---|---|---|
| state `s ∈ S` | wavefunction `Ψ ∈ ℋ` | a discrete node becomes a point in Hilbert space |
| transition `δ(sᵢ, σⱼ)` | a step of the unitary flow `U` | complex, norm-preserving; `iℏ ∂ₜΨ = ĤΨ` |
| verification step (`σ_verify`) | **einselection** (no rejection) | `U` never rejects; the environment *selects* the pointer basis |
| halt when `ψ(s) = false` | **recoherence** of a branch (astronomically rare) | leaving a world by re-interference; never forbidden |
| initial epoch `s₀` | initial wavefunction `Ψ₀`, `ψ(Ψ₀) = true` | the genesis configuration |
| terminal set `F ⊆ S` | quasi-classical set `F_ℋ ⊆ ℋ` | einselected, pointer-basis worlds |
| nested epoch `(S_sub, …, ψ_sub)` | a world, with `δ_sub^k`, `ψ_sub^k` | `Ψ` = Epoch 0 superstate; worlds = sub-epochs (illustrative — not formalized; the parent's weight is **partitioned** among children) |
| Memory `M = [(s₀,σ₁,s₁), …]` | a **forking tree** of branch-relative records | the run is no longer a single list — it splits (Everett relative state) |
| Steward (oracle, `∉ S`) | in-branch observer (`∉ ℋ` **strained**) | MWI has no "outside" — see the Steward block and `README.md` §6 |

> **Still pointwise.** MWA's `ψ` is `ψ: ℋ → {true, false}` — the continuous analogue of the *static*
> discrete invariant. It **inherits** the open problem of a dynamic / history-dependent `ψ` (§1 note;
> `README.md` §6). Decoherence is *inherently* history-dependent, so MWA is the most natural setting
> to *attempt* a trajectory-valued `ψ` — but it does **not** do so here.

> **Inherited, unresolved.** Beyond the pointwise-`ψ` problem, MWA inherits the **Born rule** (why
> `|c_k|²` should be the measure on worlds) and the **preferred-basis / factorization** problem
> (which `ℋ_S ⊗ ℋ_E` split defines a world). Both are open; see the derivation's *Open problems*.

> **Nesting is illustrative — and harder than SOL's.** `Ψ`-as-superstate / worlds-as-sub-epochs is a
> concrete instance of the §3 statechart sketch, **not** a formalization. It strains the sketch more
> than SOL: a Harel superstate persists *alongside* its substates, but here the parent branch does
> not persist beside its children — its Born weight is **partitioned among them**. Per §8, the
> `ψ_sub^k` are *evaluated independently* — a procedure, not yet a constraint (open: `README.md` §6).

**Steward constraints (branching)** — the §8 Steward block expressed for Hilbert space. Unlike §9.2 /
§10.2, the external `∉` is **strained**: MWI permits no outside, so the Steward becomes an *in-branch*
observer that forks with its world.

```
Steward ∉ ℋ                            (strained: MWI has no "outside")
Steward may query:   its own branch's relative-state record,  ψ
Steward may not:     drive U  (the unitary flow)
```

### 11.3 MWA diagram conventions

For the ASCII state-machine in the MWA derivation's "The MWA State-Machine" subsection (branching
counterpart of §6, §9.3, §10.3).

| Element | Convention | Meaning |
|---|---|---|
| Panel `HILBERT SPACE ℋ` | manifold node | the continuous (complex) state space `ℋ` |
| Box `EPOCH 0 · Ψ (superstate)` | superstate | the universal wavefunction; contains the world sub-epochs |
| Arrow `──U──▶` | unitary-flow step | forward; complex, norm-preserving (`iℏ ∂ₜΨ = ĤΨ`); contrast QNM's `∇`, SOL's `Φ_H` |
| Fork `──┬──▶ world k` | branching | one trajectory splits into worlds; each world tagged `\|c_k\|²` (Born weight) and `ψ_sub^k`; each is a sub-epoch |
| Region `F_ℋ` | quasi-classical (accepting) set | einselected, pointer-basis worlds |
| Dotted strip `ψ = false — RECOHERENCE` | epoch-ending analogue | a world re-interfering with a sibling; astronomically rare, never forbidden |
| Top band `THE ARK · the universal wavefunction Ψ` | meta-automaton (fenced) | **correspondence, not mechanism** — `U` does not verify; MWI has no "outside" (cf. `README.md` §4) |
| Bottom band `MEMORY / RECORD M` | the record (forking tree) | branch-relative records (Everett relative state); the run **splits**, it is not a single list |
| Stub `THE STEWARD` | oracle (strained) | read-only; the *in-branch* observer — itself inside `Ψ`, branches too; the external `∉ ℋ` cannot hold |

> Forward-directed, like §6, §9.3, §10.3. The retrocausal `δ*` is deliberately absent. The Ψ-as-Ark
> and observer-as-Steward labels are **motivating correspondences** (`README.md` §4) — and here the
> fencing is *forced* by the interpretation's lack of an "outside," not only by metaphor-hygiene.

---

## 12. Discrete reinterpretation (DeepSeek-V4-Pro)

The derivation
[`Discrete_Derivations/DeepSeek-V4-Pro_Epoch-Formula.md`](./Discrete_Derivations/DeepSeek-V4-Pro_Epoch-Formula.md)
instantiates the same symbols over the **discrete space of model checkpoints** of an open-weights LLM
— the first of the **discrete** derivations, and the first that is **operational** rather than
speculative. Unlike §9–§11, it does **not** reinterpret the state space as a manifold: it **reuses**
the discrete tuple `(S, Σ, δ, s₀, F, ψ)` from §1 unchanged, and instead **refines `ψ`** into three
checkable levels.

> **No glyph overload, and `σ_verify` is retained.** §9 overloads `M`; §10 and §11 swap the state
> space for `Γ` / `ℋ`. §12 does neither — `S`, `Σ`, `δ`, `s₀`, `F`, `ψ` keep their §1 meanings
> exactly. And where §9–§11 *replace* the verification gate `σ_verify` (§2) with a projection,
> conservation law, or einselection, §12 **keeps** it: `ψ` is actually evaluated at each transition.
> What is new is only the **decomposition** `ψ = ψ_int ∧ ψ_beh (∧ ψ_surf)`.

### 12.1 The DEEPSEEK Automaton — `DEEPSEEK = (S, Σ, δ, s₀, F, ψ)`

The discrete Epoch Automaton (§1) instantiated against a real model. The tuple is unchanged; the
table gives each element's realization and the three `ψ`-levels.

| Symbol | Read as | Name | Type / signature | Meaning |
|---|---|---|---|---|
| `DEEPSEEK` | "DeepSeek" | DEEPSEEK Automaton | 6-tuple | The open-model instance of the discrete machine. |
| `S` | capital **S** | Checkpoints | set | Model states in a lineage; each `s ∈ S` = weights + behavioral identity. *(The §1 `S`, unchanged.)* |
| `Σ` | capital **sigma** | Transformation alphabet | set | Transformation events: quantize, fine-tune, distill, LoRA-merge, expert-prune. *(The §1 `Σ`.)* |
| `δ` | lowercase **delta** | Transition | `δ: S × Σ → S` | Apply a transformation: `δ(s, σ) = s'`. *(The §1 `δ`.)* |
| `s₀` | "s-naught" | Sealed baseline | `s₀ ∈ S`, `ψ(s₀) = true` | The released open-weights checkpoint, sealed as genesis. |
| `F` | capital **F** | Validated terminals | `F ⊆ S` | Shipped / validated derivative checkpoints; `∅` if the lineage runs on. |
| `ψ` | lowercase **psi** | Soul invariant | `ψ: S → {true, false}` | The §1 invariant, here a conjunction: `ψ = ψ_int ∧ ψ_beh (∧ ψ_surf)`. **Pointwise** (static) — see §12.2. |
| `ψ_int` | "psi-int" | Integrity level | `ψ_int: S → {true, false}` | Checkpoint hash equals the seal — secure-boot identity of the artifact. |
| `ψ_beh` | "psi-beh" | Behavioral level | `ψ_beh: S → {true, false}` | Eval-battery scores stay within threshold `τ` of the sealed baseline. The boundary that matters. |
| `ψ_surf` | "psi-surf" | Continuous level (QNM bridge) | `ψ_surf: S → {true, false}` | Activations lie inside a learned constraint region (a representation-engineering subspace). The speculative reach toward QNM (§9). |
| `τ` | Greek lowercase **tau** | Behavioral threshold | scalar | Max tolerated per-probe deviation of `ψ_beh` from baseline; crossing `τ` is an epoch boundary. |

> **`σ_verify` is retained** (§2): it evaluates `ψ = ψ_int ∧ ψ_beh (∧ ψ_surf)` at each transition. The
> parenthesis marks `ψ_surf` as the optional, still-speculative third level — `ψ_int ∧ ψ_beh` is the
> operational core.

### 12.2 Discrete ↔ DeepSeek correspondence

The plainest mapping in the family — discrete to discrete, an *instantiation* rather than a
reinterpretation. The verification gate is kept, not replaced.

| Discrete Epoch Automaton `E` | DEEPSEEK Automaton | Note |
|---|---|---|
| state `s ∈ S` | a checkpoint (weights + behavioral identity) | the §1 state, made concrete |
| transition `δ(sᵢ, σⱼ)` | applying a transformation (quantize / fine-tune / distill) | a real engineering operation |
| verification step (`σ_verify`) | **the actual hash + eval check — *retained*** | contrast §9–§11, which replace it |
| halt when `ψ(s) = false` | the Ark refuses the transformation: new epoch, same lineage | a real, computed boundary |
| initial epoch `s₀` | the sealed baseline checkpoint, `ψ(s₀) = true` | genesis |
| terminal set `F ⊆ S` | validated / shipped derivative checkpoints | the accepting set |
| nested epoch `(S_sub, …, ψ_sub)` | MoE experts (illustrative — **weakest** in the family) | routing ≠ boundary failure; experts carry no breakable `ψ` |
| Memory `M = [(s₀,σ₁,s₁), …]` | the append-only transformation lineage + identity proofs | a **literal** log, not a correspondence |
| Steward (oracle, `∉ S`) | a read-only auditor that replays `M` and re-verifies `ψ` | **literal**; cannot drive `δ` |

> **Still pointwise.** `ψ_int`, `ψ_beh`, `ψ_surf` each test the *endpoint* checkpoint, not the path.
> So §12 **inherits** the dynamic / history-dependent `ψ` problem (§1 note; `README.md` §6). But
> unlike the manifold cases, the Ark's Memory here is an explicit append-only *trajectory* of
> transformations — the natural substrate on which to *attempt* a trajectory-valued `ψ` (the
> derivation's *Open problems*; cf. the replica test in `EPOCH-DEFINING-THE-INVARIANT.md`). Not
> attempted here.

**Steward constraints (operational)** — the §8 Steward block expressed for the checkpoint lineage.
Here it is **literal**, not strained (contrast §11) and not a correspondence (contrast §10):

```
Steward ∉ S
Steward may query:   the lineage M = [(s₀,σ₁,s₁), …],  ψ,  σ_verify
Steward may not:     drive δ  (apply or approve a transformation)
```

### 12.3 DEEPSEEK diagram conventions

For the ASCII state-machine in the derivation's "The DEEPSEEK State-Machine" subsection (the discrete
counterpart of §6, §9.3, §10.3, §11.3). The defining difference: the `σ_verify` crossing-check is
**present**.

| Element | Convention | Meaning |
|---|---|---|
| Top band `THE ARK (definer / verifier)` | meta-automaton | seals `ψ` (hash + eval battery) and runs `σ_verify` at every transformation — the gate §9–§11 omit |
| Connector label `σ_verify: ψ = ψ_int ∧ ψ_beh (∧ ψ_surf)` | verification step | `ψ` evaluated at each crossing; `true` continues, `false` is a boundary |
| Box `EPOCH n · sₙ` | state node | one checkpoint `sₙ` (`s₀` = sealed baseline) |
| Arrow `──▶` labeled `δ(sᵢ, σⱼ)` with a `σ:` tag | forward transition | a transformation (quantize, fine-tune, …) |
| Nested `MoE substates` | substate (illustrative) | active experts churn while `ψ` holds — **not** sub-epochs (no breakable `ψ`) |
| Dotted strip `ψ = false` | boundary | a transformation crosses `τ`: refused / new epoch — a **reachable** halt (contrast §9–§11's unreachable region) |
| Bottom band `MEMORY / RECORD M` | the memory | append-only transformation lineage + identity proofs (hash, eval fingerprint) |
| Stub `THE STEWARD` | oracle | read-only auditor; `∉ S`; replays `M`, re-verifies `ψ`; does not drive `δ` |

> Forward-directed, like §6, §9.3, §10.3, §11.3. The retrocausal `δ*` is deliberately absent.
> Distinctively, the `ψ = false` strip is a **reachable boundary the Ark refuses** (a real halt), not
> the "unreachable region" of §9–§11 — because here `ψ` is *checked*, not built into the dynamics.

---

### Symbol quick-index

`E` · `A` · `S` · `Σ` · `δ` · `δ*` · `δ_sub` · `s₀` · `F` · `ψ` · `ψ_sub` · `M` ·
`σ_verify` · `σ` · `s` · `s'` · `q₀` · `∈` · `∉` · `⊆` · `×` · `→` · `∧` · `⇒` · `∀` ·
`[0,1]`

**QNM (§9):** `QNM` · `M`\* · `H` · `∇` · `∇_unconstrained` · `P_ψ` · `m₀` · `F_M` · `M_ψ` ·
`m` · `m'` · `m_T`  — \*`M` is overloaded: **Memory** in §2, **configuration manifold** in §9.

**SOL (§10):** `SOL` · `Γ` · `H`† · `Φ_H` · `γ₀` · `F_Γ` · `ψ` · `Γ_ψ` · `γ` · `γ'` · `γ_T` ·
`ψ_sub^i` · `δ_sub^i`  — †`H` is the gravitational Hamiltonian here (the §9 energy functional
reused); `M` (Memory, §2) is *not* overloaded in SOL — the manifold is `Γ`.

**MWA (§11):** `MWA` · `ℋ` · `Ĥ`‡ · `U` · `Ψ` · `Ψ₀` · `F_ℋ` · `ψ` · `ℋ_S ⊗ ℋ_E` · `ρ_S` ·
`|c_k|²` · `ψ_sub^k` · `δ_sub^k` · `Ψ'` · `Ψ_T`  — ‡`Ĥ` is the Hamiltonian *operator* (hatted),
distinct from the scalar `H` of §9/§10; `M` (Memory, §2) is *not* overloaded — the state space is `ℋ`.

**DeepSeek (§12):** `DEEPSEEK` · `ψ_int` · `ψ_beh` · `ψ_surf` · `τ`  — `S` · `Σ` · `δ` · `s₀` · `F` ·
`ψ` are the §1 glyphs **reused** unchanged (no overload), and `σ_verify` (§2) is **retained** (not
replaced as in §9–§11).
