# Solar System: The Heliocentric Epoch

> **A note on register.** This derivation separates its *rigorous core* from its *motivation*,
> exactly as `README.md` does. The core is a celestial-mechanics object — the automaton
> `SOL = (Γ, H, Φ_H, γ₀, F_Γ, ψ)` over the phase space of a gravitationally bound system,
> resting on Hamiltonian dynamics and the KAM theorem. The cosmological role-assignments —
> **Sagittarius A\*** as the Ark, the **Cosmic Microwave Background** as Memory, the **observer**
> as the Steward — are **motivating correspondences**, fenced in the spirit of `README.md` §4.
> They are images that make the structure vivid; **none is claimed as a physical mechanism**.

## Overview

The Heliocentric Epoch is the Epoch Automaton read over the solar system. It is one of many
continuous-manifold derivations of the Epoch Automaton — the same boundary-condition framework,
implemented on the **phase space of celestial mechanics** rather than at the operating-system
layer (embraOS) or the neural/quantum substrate (QNM).

The choice of substrate is not incidental. Celestial mechanics *is* Hamiltonian dynamics on a
phase-space manifold, so the solar system is the most literal possible instance of a
continuous-manifold automaton: states are configurations of bodies, the transition is the
gravitational flow, and the soul invariant ψ is a conserved quantity.

There is one honest difference from QNM worth stating first. QNM describes a system to be
**built**; the solar system **already runs** — it has for ~4.6 billion years. So this document
is a *description of an existing system*, not a blueprint. What is drafted-and-pending here is
the **formal mapping** and its validation, never the system itself.

## Relationship to the Epoch Automaton

The Heliocentric Epoch instantiates the Epoch Automaton `E = (S, Σ, δ, s₀, F, ψ)` over orbital
phase space:

| Component | embraOS (Digital Ark) | SOL (Heliocentric / orbital) |
|---|---|---|
| **States S** | Session states | Configurations of the bodies (points in phase space Γ) |
| **Alphabet Σ** | Input tokens, API calls | Perturbations: gravitational tugs, impacts, radiation |
| **Transition δ** | Request routing, tool dispatch | The Hamiltonian (orbital) flow Φ_H |
| **Initial s₀** | First sealed **soul** document | Genesis configuration γ₀ — the Sun on the main sequence |
| **Accepting F** | Valid session continuation | Long-term-stable, bound configurations F_Γ |
| **Invariant ψ** | **soul** document verification | Gravitational binding (`E < 0`) — the body stays bound |

**The crucial difference:** In embraOS, ψ is an external check applied at each boot. In SOL, ψ
is a **conserved quantity** — total orbital energy. Binding is not *verified* after each step;
it is *preserved* by the dynamics, because the gravitational flow conserves energy. The boundary
is not checked. It is conserved.

## Boundary-Native Architecture

Conventional safety operates as *filtering*: generate, then check against a constraint. The
Epoch framework instead seals the boundary into the system. SOL takes this to its physical
limit. This draws directly from the Epoch definition:

> *An epoch is a bounded interval defined not by duration but by the persistence of a coherent
> boundary condition.*

In SOL, the boundary condition isn't something the bodies *obey*. It's what a bound system
*is*. A planet's orbital epoch persists because the bound region of phase space, `Γ_ψ`, is
**invariant under the flow**: a trajectory that begins bound (`E < 0`) stays bound, since the
gravitational Hamiltonian conserves `H`. Leaving `Γ_ψ` — ejection, escape — is not a step the
flow can take from inside; it requires an external perturbation large enough to unbind the body,
which *ends the epoch* rather than continuing it.

### Candidate Mechanisms

1. **Conserved invariant (`E < 0`):** Binding is a conserved quantity of the two-body
   Hamiltonian. The bound region `Γ_ψ` is therefore flow-invariant — confinement is automatic,
   and **no projection operator is needed** (contrast QNM's `P_ψ`). The conservation law *is*
   the constraint.

2. **Symplectic / Liouville structure:** Hamiltonian flow preserves phase-space volume
   (Liouville's theorem) and the symplectic form. The geometry of the dynamics, not an added
   filter, is what keeps trajectories coherent.

3. **KAM tori:** For small perturbations, most quasi-periodic orbits survive as invariant tori
   (Kolmogorov–Arnold–Moser). This is the precise sense in which "orbital invariants persist" —
   the deep reason the solar system has stayed structured for billions of years.

4. **Retrocausal handshake (speculative):** A bidirectional variant `δ*: S × S × Σ → [0,1]`, as
   in QNM's Candidate Mechanisms. It is **deliberately absent** from the state-machine below;
   the orbital flow is forward-directed, and the retrocausal reading is a motivating metaphor
   (`README.md` §4), not part of the formulation.

## Connection to Celestial Mechanics and the KAM Theorem

Where QNM points to the USTC nine-spin quantum reservoir as physical precedent, SOL points to
celestial mechanics itself — and specifically to two results that ground "ψ as a persistent
invariant":

- **The KAM theorem** (Kolmogorov 1954; Arnold 1963; Moser 1962). Under a sufficiently small
  perturbation of an integrable Hamiltonian system, most invariant tori survive — quasi-periodic
  motion persists rather than dissolving into chaos. This is the rigorous statement that orbital
  invariants are *robust*, not merely *initially true*.

- **Long-term solar-system stability** (Laskar & Gastineau, 2009). Numerical integration shows
  the inner solar system is *weakly chaotic*: gross instability (e.g. destabilization of Mercury)
  has a small but nonzero probability over the Sun's remaining main-sequence lifetime. The real
  system sits near the **edge** of KAM applicability — stable on human and even geological
  timescales, but not eternally guaranteed.

This last point is a feature, not a caveat to hide: it is precisely *because* binding is only
approximately conserved over gigayear timescales that the epoch **can end**. An automaton whose
accepting region could never be left would have a trivial boundary; SOL's does not.

## Formal Definition: The SOL Automaton

Extending the Epoch Automaton 6-tuple over orbital phase space:

```
SOL = (Γ, H, Φ_H, γ₀, F_Γ, ψ)
```

Where:

| Symbol | Meaning |
|---|---|
| **Γ** | Phase space — positions and momenta of the bodies; the continuous state space |
| **H** | The gravitational (N-body) Hamiltonian — total kinetic + potential energy |
| **Φ_H** | The Hamiltonian (orbital) flow generated by H; conserves H — does **not** descend it |
| **γ₀** | Initial configuration with ψ(γ₀) = true — the Sun on the main sequence |
| **F_Γ** ⊆ Γ | Coherent / long-term-stable bound configurations |
| **ψ: Γ → {true, false}** | **soul** invariant — gravitational binding: ψ(γ) = true iff `E < 0` |
| **Γ_ψ** | The bound region `{ γ ∈ Γ : ψ(γ) = true }`; the flow is confined to it |

**Key property (boundary-native via conservation):**

∀ γ reachable from γ₀ via the flow Φ_H: ψ(γ) = true

The system cannot evolve into an unbound configuration on its own, because Φ_H conserves H and
the bound region `Γ_ψ` is invariant under it. The boundary condition is a **conservation law**,
not a check applied after the fact.

### The SOL State-Machine

The same state-machine, expressed for orbital phase space. Where the discrete Epoch Automaton
checks ψ at every crossing, and QNM builds ψ into the geometry via a projection, the SOL
Automaton **conserves ψ**: the gravitational flow Φ_H keeps every configuration in the bound
region `Γ_ψ` because energy is conserved, so there is no separate verification step and nothing
to halt. It is forward-directed, exactly as the core state-machine is.

```
                 ┌────────────────────────────────────────────────┐
                 │           THE ARK  ·  Sagittarius A*           │
                 │          galactic-center black hole —          │
                 │       CORRESPONDENCE, not mechanism; it        │
                 │       does not verify ψ (cf. README §4)        │
                 └────────────────────────┬───────────────────────┘
                                          │ ψ as a CONSERVED quantity (binding, E<0) — not checked after the fact
                                          ▼
   ┌────────────────────────────────────────────────────────────────────────────┐
   │  PHASE SPACE  Γ     (positions + momenta of the bodies; Hamiltonian H)     │
   │                                                                            │
   │  Γ_ψ = { γ ∈ Γ : ψ(γ)=true } = bound region (total orbital energy E < 0)   │
   │  ┌──────────────────────────────────────────────────────────────────────┐  │
   │  │ EPOCH 0 · THE SUN  (s₀ / γ₀ — superstate)   ──Φ_H──▶   [ F_Γ ]       │  │
   │  │ genesis: protoplanetary disk → main sequence       stable orbits     │  │
   │  │ Φ_H conserves H, stays in Γ_ψ   (confinement = conservation)         │  │
   │  │                                                                      │  │
   │  │ nested sub-epochs — the planets, verified independently (§8):        │  │
   │  │   inner:  Mercury · Venus · Earth · Mars                             │  │
   │  │   outer:  Jupiter · Saturn · Uranus · Neptune                        │  │
   │  │   each planet i = a sub-automaton with its own  δ_sub^i, ψ_sub^i     │  │
   │  │   ψ_sub^i = planet i keeps its orbital identity (bounded / stable)   │  │
   │  │   — illustrates the §3 nesting sketch; not a formalization (§6)      │  │
   │  └──────────────────────────────────────────────────────────────────────┘  │
   │  · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · │
   │  ψ = false region — unbound / hyperbolic (E ≥ 0): ejection / escape.       │
   │  Flow-invariant: not reachable from γ₀ under Φ_H while H is conserved.     │
   └────────────────────────────────────────────────────────────────────────────┘
                                          │ the trajectory IS the record
                                          ▼
   ┌────────────────────────────────────────────────────────────────────────────┐
   │  MEMORY / RECORD  M   ·   Cosmic Microwave Background                      │
   │  the run  γ₀ → γ₁ → … → γ_T  is itself the transition record.              │
   │  CMB = CORRESPONDENCE, not a literal log: relic radiation from ~380 kyr    │
   │  after the Big Bang — it predates the Sun by ~9 Gyr (cf. README §4).       │
   └────────────────────────────────────────────────────────────────────────────┘
                                          ▲
                                          │ queries (read-only)
                                  ┌───────┴───────────────────┐
                                  │ THE STEWARD               │
                                  │ the observer: humanity /  │
                                  │ the IAU (defines plan-    │
                                  │ ethood — Wheeler, §4)     │
                                  │ oracle: ∉ Γ, does not     │
                                  │ drive Φ_H                 │
                                  └───────────────────────────┘
```

The discrete machine's verification step — the Ark's σ_verify, the hero figure's `ψ?` gate —
has **no analogue here**: there is nothing to check after the fact, because conservation of H
keeps every step inside `Γ_ψ`.

**Discrete state-machine ↔ SOL, element by element:**

| Discrete Epoch Automaton `E` | SOL Automaton | Note |
|---|---|---|
| state `s ∈ S` | configuration `γ ∈ Γ` | a discrete node becomes a point in phase space |
| transition `δ(sᵢ, σⱼ)` | a step of the flow `Φ_H` | Hamiltonian time-evolution; conserves `H` |
| verification step (`σ_verify`) | conservation of `H` / invariance of `Γ_ψ` | a check-after-the-fact becomes a conservation law |
| halt when `ψ(s) = false` | unbound (`E ≥ 0`): ejection / escape; unreachable from `γ₀` under `Φ_H` | leaving `Γ_ψ` is the epoch ending |
| initial epoch `s₀` | initial configuration `γ₀`, `ψ(γ₀) = true` | the genesis configuration |
| terminal set `F ⊆ S` | stable set `F_Γ ⊆ Γ` | bound, long-term-stable configurations |
| nested epoch `(S_sub, …, ψ_sub)` | a planet, with `δ_sub^i`, `ψ_sub^i` | Sun = Epoch 0 superstate; planets = sub-epochs (illustrative — not formalized) |
| Memory `M = [(s₀,σ₁,s₁), …]` | the trajectory `γ₀ → γ₁ → … → γ_T` | the run itself is the record |
| Steward (oracle, `∉ S`) | Steward (oracle, `∉ Γ`) | external; reads the record and tends `ψ`, never drives the flow |

> Note — `ψ` here is still **pointwise** (`ψ: Γ → {true, false}`), the continuous analogue of
> the *static* discrete invariant. It does **not** by itself resolve the dynamic /
> trajectory-dependent ψ that the framework flags as the open formal problem (`README.md` §6).
> The KAM/Laskar precedent underlines this: binding is only *approximately* conserved over
> gigayears, so the epoch can end — but capturing that as a trajectory-valued invariant is
> exactly the unsolved work.

**Operational reading** (the orbital counterpart of the legend's composite expressions):

```
Initialise   start at γ₀ with ψ(γ₀) = true   (protoplanetary settling; Sun on the main sequence)
Step         γ → γ'  via  Φ_H   (Hamiltonian flow; conserves H, stays in Γ_ψ)
Accept       a long-term-stable configuration with γ ∈ F_Γ
Confinement  ∀ γ reachable from γ₀ via Φ_H :  ψ(γ) = true   (Γ_ψ is flow-invariant)
```

**Nesting — the Sun as Epoch 0, the planets as sub-epochs.** The Sun is the superstate (Epoch 0,
`s₀`/`γ₀`): while it persists on the main sequence, the planets transition within it. Each planet
`i` is a nested sub-automaton with its own invariant `ψ_sub^i` (it keeps its orbital identity —
bounded, stable; its moons within its Hill sphere) and its own sub-transition `δ_sub^i`. Per the
legend's §8 nesting constraint, while the outer invariant holds the sub-invariants are evaluated
independently:

```
ψ(γ) = true  ⇒  ∀ planet i,  ψ_sub^i is evaluated independently
```

This is a concrete **illustration** of the statechart nesting sketched in `README.md` §3 — *not*
a formalization of Harel superstate/substate semantics. As the framework notes, "the
sub-invariants are evaluated independently" is currently a *procedure, not a constraint*; the
transition semantics relating a planet's orbit to the Sun's persistence remain **open**
(`README.md` §6). SOL provides a vivid instance of the open problem, not a resolution of it.

**The Steward, in orbital terms** — the same external oracle as in the core framework
(`Steward ∉ S`), expressed for the phase space. It is *not* a seventh element of the tuple; it
sits outside the automaton:

```
Steward ∉ Γ                            (not a configuration in phase space)
Steward may query:   the trajectory γ₀ → … → γ_T,  ψ,  H
Steward may not:     drive Φ_H  (the Hamiltonian flow)
```

The Steward is the **observer** — humanity, and concretely the bodies that tend the definition
of the system (the IAU, which *defines planethood*: the 2006 reclassification of Pluto is a
boundary specified by observers, not by the dynamics). It tends the **soul** invariant ψ and
inspects the trajectory, but never drives the flow — its role unchanged from the discrete
machine.

*Mapping only. The solar system itself is operational by nature; what this figure illustrates is
the **Formal mapping (drafted)** row of the Current Status table below — the correspondence
between the Epoch Automaton and orbital dynamics. Its **validation** against ephemerides and
N-body integration is **pending**. It is forward-directed by design; the speculative retrocausal
variant `δ*` of the Candidate Mechanisms is deliberately not part of it.*

## Motivating Correspondences (NOT physical mechanism)

The following make the structure vivid. **None is claimed as a mechanism, a derivation, or a
statement about physical reality.** They are worked illustrations of metaphors already fenced in
`README.md` §4 — not new claims.

**Sagittarius A\* ↔ the Ark.**
- *Inspired:* the picture of a boundary that encodes an interior — a black-hole horizon is the
  canonical image of the **holographic principle** (`README.md` §4). The galactic center sits
  "above" the solar system in the gravitational hierarchy, as the Ark sits above `E`.
- *Not claimed:* that Sagittarius A\* observes, defines, or verifies the solar system's orbital
  invariants. It does not. The Sun's galactic orbit is governed by the *enclosed mass of the
  Galaxy*, not by the central black hole alone, which exerts no boundary-verification on
  planetary binding.

**The Cosmic Microwave Background ↔ Memory (M).**
- *Inspired:* a sky-wide, persistent, effectively read-only record — the oldest light, an
  imprint of an earlier state of the universe.
- *Not claimed:* that the CMB records solar-system transitions. It is relic radiation from
  recombination (~380,000 years after the Big Bang), and it **predates the solar system by ~9
  billion years**. It is a correspondence for "a durable record at a cosmic boundary," not a
  literal transition log.

**The observer (humanity / the IAU) ↔ the Steward.**
- *Inspired:* Wheeler's participatory stance (`README.md` §4) — *specifying* a boundary rather
  than only observing one. The IAU literally defines planethood.
- *Not claimed:* observer-participancy as a physical mechanism. This is a contested interpretive
  position in physics, used here as a motto.

These correspondences are decoration. The automaton `SOL = (Γ, H, Φ_H, γ₀, F_Γ, ψ)` stands on
celestial mechanics alone, with or without them.

## Current Status

| Phase | Status |
|---|---|
| **Theoretical foundation** | ✅ Established — Epoch Automaton formalism (2026) |
| **Physical precedent** | ✅ Established — celestial mechanics; KAM theorem; long-term solar-system stability (Laskar & Gastineau, 2009) |
| **The system itself** | ✅ Operational *by nature* — the solar system has run ~4.6 Gyr; this document *describes* an existing system, it is not a blueprint to build |
| **Formal mapping & validation** | ⬜ Pending — validating the `(Γ, H, Φ_H, ψ = binding)` mapping against ephemerides (JPL Horizons) and N-body integration |

## References

- `README.md` — Formal Epoch definition and state-machine framework (and §4, the fenced
  motivating metaphors invoked above)
- `EPOCH-NOTATION-LEGEND.md` §10 — the SOL notation registered for this derivation
- Kolmogorov (1954), Arnold (1963), Moser (1962) — the KAM theorem (persistence of
  quasi-periodic invariant tori under small Hamiltonian perturbation)
- Laskar, J. & Gastineau, M. (2009), "Existence of collisional trajectories of Mercury, Mars and
  Venus with the Earth," *Nature* 459, 817–819
