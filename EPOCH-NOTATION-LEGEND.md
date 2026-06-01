# EPOCH — Notation Legend

A reference for the mathematical notation, type signatures, and diagram conventions
used in the state-machine sections of [`EPOCH-PROJECT.md`](./EPOCH-PROJECT.md) (§2–§4,
§5.1) and the state-machine diagram in
[`EPOCH-HIGH-LEVEL-EXPLANATION.md`](./EPOCH-HIGH-LEVEL-EXPLANATION.md).

## How to read it

Everything reduces to **two tuples** and the functions that operate on them: the
**Epoch Automaton** `E` (what an epoch *is*) and the **Ark** `A` (what observes, records,
and verifies `E`). After that it's just decoration:

- **Numeric subscripts** name specific instances in a sequence — `s₀, s₁, s₂` / `σ₁, σ₂`.
- **The subscript `_sub`** marks something belonging to a nested sub-automaton.
- **A prime `'`** names a second state distinct from `s` (its role is positional — see the [caveat](#a-caveat-the-prime--is-positional)).
- **A superscript `*`** marks the backward/retrocausal variant of a function (`δ*`).

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
| §4.2 (Valid Continuation) | `δ(s', σ) = s` | **`s'`** | `s` |
| §4.6 (Retrocausal) | `δ(s, σ) = s'` | `s` | **`s'`** |

**Rule of thumb:** read the direction off the `δ(input, σ) = output` form *every time*.
Never assume the primed symbol is "the next state" — in §4.2 it's the previous one.

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

For the ASCII state-machine diagram in §3 of `EPOCH-PROJECT.md`.

| Element | Convention | Meaning |
|---|---|---|
| Box labeled `EPOCH n / (sₙ)` | state node | one epoch-state `sₙ` |
| Solid arrow `──▶` labeled `δ(sᵢ, σⱼ)` | forward transition | causal; `δ` applied — standard automaton direction |
| Return arrow `◀──` labeled `δ*(sᵢ, σⱼ)` | backward negotiation | retrocausal handshake (Cramer transactional model) |
| Branch `ψ(s)=true? / ψ(s)=false?` | guard / verification fork | the boundary check gating every crossing — `true` continues, `false` halts |
| Nested box `SUB-EPOCH (nested)` | substate | a sub-automaton inside a superstate (Harel statechart) |
| Top band `THE ARK (meta)` | meta-automaton | observes · records · verifies; sits above `E`, not inside it |
| Bottom band `MEMORY / RECORD` | the memory `M` | transition history · identity proofs · state snapshots |

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

The key conditions from §4, in plain language.

**Valid continuation** (§4.2) — `s` is a legitimate next epoch after `s'`:

```
δ(s', σ) = s   ∧   ψ(s) = true
```
The transition is defined **and** the resulting epoch satisfies the soul invariant.

**Halt** (§4.2) — the epoch terminates with no successor:

```
δ(s', σ) = s   ∧   ψ(s) = false
```
The transition is defined, but the resulting epoch fails the invariant; the Ark refuses
it.

**Nesting constraint** (§4.3) — interior invariants are checked separately:

```
ψ(s) = true  ⇒  ∀ s_sub ∈ S_sub, ψ_sub(s_sub) is evaluated independently
```
While the superstate's invariant holds, every interior substate is verified against its
own `ψ_sub`, independent of the outer `ψ`.

**Retrocausal completion** (§4.6) — a boundary crossing fully resolves:

```
δ(s, σ) = s'   ∧   δ*(s', s, σ) > 0   ∧   ψ(s') = true
```
Forward transition defined, backward handshake has nonzero amplitude, **and** the target
epoch satisfies the invariant.

**Steward / oracle constraints** (§4.5):

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

### Symbol quick-index

`E` · `A` · `S` · `Σ` · `δ` · `δ*` · `δ_sub` · `s₀` · `F` · `ψ` · `ψ_sub` · `M` ·
`σ_verify` · `σ` · `s` · `s'` · `q₀` · `∈` · `∉` · `⊆` · `×` · `→` · `∧` · `⇒` · `∀` ·
`[0,1]`

**QNM (§9):** `QNM` · `M`\* · `H` · `∇` · `∇_unconstrained` · `P_ψ` · `m₀` · `F_M` · `M_ψ` ·
`m` · `m'` · `m_T`  — \*`M` is overloaded: **Memory** in §2, **configuration manifold** in §9.
