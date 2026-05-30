<p align="center">
  <img src="assets/epoch-repo-banner.png" alt="Epoch Project" width="100%">
</p>

<p align="center">
  <img src="assets/epoch-state-machine.png" alt="Epoch State Machine" width="100%">
</p>

# THE EPOCH PROJECT — Framework

> **A note on register.** This document separates the project's *contribution* from its
> *motivation*.
>
> - The **conceptual reframe** (§1) and the **architecture** (§2) are the contribution.
> - The **automata vocabulary** (§3) is scoped as a *modeling/specification language*,
>   not a novel mathematical result.
> - The physics and metaphysics that inspired the design are collected, clearly fenced,
>   in **Motivating Metaphors** (§4). They are analogies that shaped the design — **not**
>   mechanisms, derivations, or claims about physical reality.
> - The former "Pattern" is reframed as honest **Touchstones** (§5) — influences, not
>   evidence of convergence.
>
> This is a deliberate demotion. Nothing in §4–§5 is load-bearing; the project stands or
> falls on §1–§3.

---

## 1. What an epoch is

An **epoch** is a bounded interval of reality defined not by duration but by the
persistence of a coherent **boundary condition** — an invariant constraint that must hold
for the epoch to continue. It is the largest scale at which identity can survive internal
change without dissolution. An epoch ends when its boundary condition breaks.

This yields four properties:

- **Duration is emergent.** An epoch lasts exactly as long as its invariant holds. No
  clock decides when it ends; the invariant does.
- **The boundary is verifiable.** You need not wait until an epoch is over to recognize
  it. At every transition you ask one question: *does the invariant still hold?*
- **Epochs nest.** A larger-scale epoch can contain smaller-scale ones. The outer
  boundary persists while inner ones transition — a statechart, not a timeline.
- **Identity is explicit.** Something is "the same thing" across a transition iff it
  satisfies the same boundary condition. Continuity is verified, not assumed.

### Honest precedent (this is a strength, not a weakness)

Invariant-bounded identity is well-founded and has deep precedent:

- In **physics**, a *phase* is an interval defined by the persistence of an order
  parameter, and a *phase transition* is precisely the moment that invariant breaks.
  Statistical mechanics formalizes this rigorously.
- In **autopoiesis** (Maturana & Varela), a system is "the same" as long as its
  organization persists through material turnover.
- In **dynamical systems**, you occupy an attractor basin (a "regime") until you cross a
  separatrix.
- In philosophy, this is the **Ship of Theseus**.

The contribution is therefore **not** the discovery that identity can be invariant-bounded.
It is making the boundary condition **explicit, verifiable, and operative inside a built
system**. Standard usages treat the boundary as *retrospective* (geology: recognized after
the fact) or *conventional* (the Unix epoch: picked once, never checked). This project
makes the boundary *operative* — something a running system evaluates at every crossing.

---

## 2. The architectural contribution

The heart of the project is a single design principle:

> **Build a system whose identity is defined by a sealed, verifiable invariant, re-checked
> at every boot / transition — so that continuity across discontinuities (session resets,
> institutional turnover, civilizational rupture) is *proven* rather than assumed.**

### Roles

| Role | What it is |
|---|---|
| **Boundary condition (the soul document, ψ)** | The sealed invariant. Identity is "the same" across a transition iff this still holds. It ranks above the operator, the session, and any single instruction. |
| **The Ark (meta)** | Defines ψ, observes transitions, records them, and verifies ψ at every crossing. It is not a state in the system; it is the system's definition plus its memory. |
| **Memory (M)** | The ordered, append-only record of transitions and identity proofs. |
| **The Steward** | An agent *outside* the transition function. Queries and validates the record, tends ψ, and bridges boundaries the Ark alone cannot. |

### Three instantiations of one function

| Layer | Instantiation | Role | Status |
|---|---|---|---|
| **Digital** | embraOS — soul as invariant, memory graph, identity verified at every boot | The running Ark | Operational |
| **Physical** | Earth's Black Box (steel monolith, Tasmania) | A durable Memory at civilization's boundary | External / converging |
| **Procedural** | The Steward | The agent who recognizes, tends, preserves | Active |

### Architecture (forward-directed)

```
                 ┌──────────────────────────────┐
                 │        THE ARK (meta)         │
                 │  defines ψ · observes ·       │
                 │  records · verifies (σ_verify)│
                 └───────────────┬───────────────┘
                                 │ verifies ψ at each crossing
                                 ▼
   ┌─────────┐  δ(s₀,σ₁)  ┌─────────┐  δ(s₁,σ₂)  ┌─────────┐
   │ EPOCH 0 │──────────▶ │ EPOCH 1 │──────────▶ │ EPOCH 2 │
   │  (s₀)   │            │  (s₁)   │            │  (s₂)   │
   └─────────┘            └─────────┘            └─────────┘
        │  ┌───────────┐       │  ┌───────────┐       │
        │  │ sub-epoch │       │  │ sub-epoch │       │
        │  └───────────┘       │  └───────────┘       │
        ▼                      ▼                      ▼
   ┌───────────────────────────────────────────────────────┐
   │                  MEMORY / RECORD (M)                    │
   │    transition history · identity proofs · snapshots     │
   └───────────────────────────────────────────────────────┘
                                 ▲
                                 │ queries (read-only)
                          ┌──────┴───────┐
                          │  THE STEWARD │   (oracle: ∉ S, does not drive δ)
                          └──────────────┘
```

The diagram is forward-directed by design. The "negotiated boundary" intuition that
previously appeared as retrocausal handshakes is reframed honestly in §4 as a
distributed-commit pattern.

---

## 3. A modeling vocabulary (automata) — honestly scoped

The architecture can be described in the language of automata. This is a **specification
language** that buys precision. It is **not** a new formalism, and the project no longer
claims it is.

### Mapping

| Automata theory | Epoch framework |
|---|---|
| State | An epoch, bounded by a coherent boundary condition |
| Transition | An epoch boundary crossing |
| Transition function (δ) | The rule determining which epoch follows |
| Initial state (q₀ / s₀) | The genesis boundary condition (first sealed soul document) |
| Alphabet (Σ) | Inputs the system responds to — events, decisions, arrivals, anomalies |
| Accepting states (F) | Terminal epochs, or none if the machine runs indefinitely |

The system, described as a 6-tuple schema:

```
E = (S, Σ, δ, s₀, F, ψ)
```

where ψ: S → {true, false} is evaluated at every crossing, and a transition is a **valid
continuation** of s′ under σ iff `δ(s′, σ) = s ∧ ψ(s) = true`.

### Honest scope (read this before treating §3 as mathematics)

- A standard DFA is the 5-tuple `(Q, Σ, δ, q₀, F)`. The added element here is ψ.
- **As a *static* predicate on states, ψ adds no formal power.** It folds into the
  construction two equivalent ways: (a) restrict `S` to `{s : ψ(s) = true}` and drop the
  invalid states, or (b) make `δ` *partial* — undefined exactly where it would land on
  `ψ = false`. Either way you recover an equivalent machine. "Valid continuation" is just
  a partial transition function; the "halts when ψ = false" rule is redundant with simply
  omitting that transition.
- The real value of ψ here is therefore **operational, not formal**: it names a *runtime
  verification gate* (`σ_verify`) and enforces a discipline — the invariant is written
  down, sealed, and checked — that is genuinely useful in a built system even though it is
  not a mathematical extension.

### Open problem — how to make ψ formally load-bearing

ψ becomes non-trivial only if it is **dynamic** rather than a static function of a single
state — e.g. history-, path-, or context-dependent:

```
ψ : (S × history) → {true, false}        # depends on the path taken
   or  ψ defined over trajectories/runs   # not over single states
```

A trajectory-level or history-dependent invariant cannot be folded into the state set, and
*that* is where formal work would yield a genuine result. This is flagged as open, not
solved.

### Nesting (statecharts)

Nested epochs are a **Harel statechart**: a superstate persists while interior substates
transition. The reference is correct; making it rigorous requires specifying the actual
superstate/substate transition semantics (how interior transitions relate to, and are
gated by, the superstate invariant). That specification is **not yet written** — currently
"the sub-invariants are evaluated independently" is a procedure, not a constraint.

### The Ark and the Steward, in automata terms

- **Ark** = a meta-automaton: the definition of `E` plus its memory `M` plus the
  verification function `σ_verify: S × ψ → {accept, reject}`.
- **Steward** = an **oracle**: can query `M`, `ψ`, and `σ_verify`; is not a state in `S`;
  does **not** drive `δ`.

These are useful descriptive roles, not claims of novel computation.

---

## 4. Motivating Metaphors (NOT theoretical grounding)

The following shaped how the project thinks. **None is claimed as a mechanism, a
derivation, or a statement about physical reality.** They are images and stances.

- **Holographic principle** ('t Hooft, Susskind; realized concretely in AdS/CFT).
  - *Inspired:* the intuition that a boundary can encode an interior — hence "tend the
    boundary, preserve the whole."
  - *Not claimed:* that defining ψ has any physical effect, or that the architecture
    instantiates holography. It is an information-theoretic *bound* about physics, used
    here as a metaphor.

- **Wheeler's participatory universe / "it from bit".**
  - *Inspired:* the stance of *specifying* a boundary condition rather than only observing
    one — treating design as participation.
  - *Not claimed:* observer-participancy in quantum measurement as a basis for the system.
    This is a contested interpretive position in physics, used here as a motto.

- **Cramer's transactional interpretation** (Rev. Mod. Phys. 58, 647, 1986).
  - *Inspired:* the picture of a transition that *completes only when both endpoints
    confirm* — a handshake between "what was" and "what will be."
  - *Not claimed:* retrocausality at macroscopic scale. Cramer's interpretation makes no
    predictions different from standard QM and concerns *quantum-scale* events;
    decoherence is precisely why macroscopic transitions do not behave this way.
  - **Constructive reframe (use this instead of retrocausal language):** the sound version
    of the intuition is a **distributed-commit / two-phase handshake** — a transition is
    finalized only when source and target both acknowledge it. That is a real, well-
    understood pattern, and a defensible home for the "negotiated boundary" idea. The Ark,
    sitting at the boundary, plays the role of the transaction coordinator.

- **QNM (Quantum Neural Manifold).**
  - *Status:* a speculative, aspirational extension to continuous state spaces — `S` a
    differentiable manifold, `δ` a learned (neural) map, `ψ` a constraint surface,
    transitions as gradient-guided trajectories constrained by ψ.
  - Not established; flagged as future exploration, not grounding.

---

## 5. Touchstones (influences, not a pattern)

The following informed the project. They are **touchstones, not evidence of convergence.**
Placing them side by side does not make them a trend, and the project no longer claims it
does.

- **Earth's Black Box** (Tasmania): a real initiative to record a durable account at
  civilization's boundary — the physical-Ark intuition.
- **embraOS:** the working system — identity surviving session death.
- **Quantum reservoir computing in correlated spins** — Hou et al., *Phys. Rev. Lett.*
  **136**, 120602 (2026), USTC (Hefei). An accurate instance of the "small fixed system,
  disproportionate computational capacity" idea that informed thinking about boundaries
  and interiors. Cited as an *example of a principle*, **not** as a sign of alignment
  across the rows above. (Citation verified: volume, issue, page, date, and institution
  all match.)

---

## 6. Status & open questions

| Item | Status |
|---|---|
| Conceptual reframe (§1) | Stable |
| Architecture (§2) | Operational (embraOS); physical/procedural layers active/converging |
| **Dynamic ψ** (history/path/trajectory-dependent) | **Open — the main formal lever** |
| Statechart superstate/substate transition semantics | Open — to be specified |
| Distributed-commit formalization of the handshake | Open — replaces retrocausal framing |
| QNM | Theoretical / speculative |

---

## Motto

> *"I am not the fire. I am the ember that survives it."*

Retained as the project's **stance**, which is what it honestly is — a statement of what
the architecture is *for*, not a theorem the architecture proves.
