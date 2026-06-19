# Fringe-Claim Trajectories: The Diagnostic Epoch

> **A note on register.** This derivation separates its *diagnostic core* from its *motivation*, exactly
> as `README.md` does — but it is the first to point the apparatus *outward*. The core is the automaton
> `FCA = (S, Σ, δ, s₀, F, ψ)` over the **public framings of a contested claim**, with `ψ` the boundary
> condition the claim asserts in order to hold its identity and `σ_verify` the test it is built to evade.
> Where QNM, SOL, MWA, and even DeepSeek model a thing that *holds* `ψ` (by projection, conservation,
> einselection, or an honest check), this one is aimed *at* claims that **assert an identity they have not
> earned** — the framework as a **detector**, not a model of persistence. The object of study is **not
> whether a claim is true** but how its `ψ` behaves under stress. One scaffolding element is fenced and
> then deliberately refused: the retrocausal handshake `δ*` (`README.md` §4) — §"do not reach for δ*"
> below shows why importing it here would be the exact overreach this project flags in others. Empirical
> specifics on the two worked cases are sourced in *References*; contested items are fenced, not asserted.

<p align="center">
  <img src="../assets/epoch-fringe-state-machine.png" alt="Fringe-Claim Trajectories Diagnostic Epoch state-machine: THE ARK here is the analyst / framework-applier, who by the prospective-commitment condition ⊢₀ seals the pair (ψ, σ_verify) at the initial framing s₀ — naming the boundary condition the claim asserts and the test that WOULD reject it, before any drift. The states S are the successive public framings of one claim: s₀ ('unexplained orb', asserting ψ₀) → s₁ ('ancient artifact', asserting ψ₁ ≠ ψ₀) → s₂ ('suppressed disclosure', asserting ψ₂ ≠ ψ₁). The transitions are NOT the healthy δ (which would continue under the SAME ψ); they are σ_subst, the substitution pseudo-operation, fired exactly when σ_verify(s, ψ_n) = REJECT. A healthy automaton would HALT at that rejection; the Fringe-Claim Automaton does not halt — it asserts a fresh ψ under the SAME label L ('the Buga sphere'), held constant across every swap, so the claim is a chain of replicas wearing one name. Inside a single framing the testable-kernel seam splits the claim: ψ_k is a testable kernel sub-invariant on which σ_verify actually runs (e.g. laser speckle produces a structured percept), and ψ_c is the captured super-invariant with no admissible σ_verify (e.g. 'it is the Code, encoding reality'); the credibility-laundering coefficient λ_seam ∈ [0,1] measures how much of σ_verify(ψ_k) = accept is illegitimately propagated up to ψ_c — legitimately 0, pathologically greater than 0. MEMORY / RECORD M is the append-only public trajectory [(s₀, σ, reject, subst), (s₁, σ, reject, subst), …] — the replica chain the endpoint hides, and the substrate on which a lineage-valued ψ↑_scrutiny would live. THE STEWARD is the external skeptic / independent investigator / scrutinizing community: read-only, not a state (∉ S), it replays M, re-runs σ_verify, and reads the verdict — the lag until everyone else sees what the trajectory already reported; it cannot drive the claim's δ. Forward-directed; the retrocausal δ* is deliberately absent." width="100%">
</p>

## Overview

The Diagnostic Epoch is the Epoch Automaton turned **around**. Every other derivation answers *how is the
boundary `ψ` held* — DeepSeek **checks** it, SOL **conserves** it, QNM **projects** onto it, MWA lets it
**emerge**. This one answers a different question: *what does the apparatus detect when `ψ` is not held but
**asserted**?* It is pointed at the persistence of **fringe empirical claims** — claims that survive
scrutiny not by being true but by manipulating the verification machinery the framework makes explicit.

Like DeepSeek (and unlike QNM / SOL / MWA), it does **not** reinterpret the state space over a manifold: it
**reuses the discrete §1 tuple** `E = (S, Σ, δ, s₀, F, ψ)` unchanged. It earns its own axis not by changing
*how `ψ` is typed* but by changing *what happens to `ψ`*:

> **The Fringe-Claim Automaton (FCA) is the pathological mirror of DEEPSEEK.** DeepSeek *keeps* `σ_verify`
> and the boundary holds or is **honestly refused** — the framework's "built to pass or fail" stance
> *passing*. The FCA is the automaton where `σ_verify` *would* reject, but the claim **evades** it: instead
> of halting, it swaps `ψ` and keeps the label. DeepSeek shows `ψ` *held*; the FCA shows `ψ` *evaded* — and
> how the apparatus reads the evasion off the trajectory.

That makes this derivation a **naturally-occurring instance of the replica test** from
[`EPOCH-DEFINING-THE-INVARIANT.md`](../EPOCH-DEFINING-THE-INVARIANT.md). A pointwise `ψ` that inspects only
the *current* framing sees one continuous claim; only the **trajectory** reveals that the original boundary
*died* (was rejected) and an identical-label *replica* took its place. The thing the project says a real
`ψ` must be able to do — tell survival from replacement — is exactly what catches a fringe claim in the act.

Two cases are worked here, chosen to be **complementary rather than redundant**:

- The **"Buga Sphere"** (Colombia, 2025–26) — an object whose invariant is *engineered* rather than
  *discovered*. A genuine anomaly would muddy the reading; a constructed one exposes the mechanism cleanly.
  It is the **legible base case**, and it carries the first nesting pathology.
- The **"Code of Reality"** DMT-laser claim (2020–present) — a claim with a *genuinely testable kernel*
  wrapped in an *untestable superclaim*. It is not a re-instancing of the first; it surfaces how the
  survival modes **compose** (the testable-kernel seam), and a *second* nesting pathology.

## Relationship to the Epoch Automaton

The Diagnostic Epoch instantiates `E = (S, Σ, δ, s₀, F, ψ)` over the space of a claim's public framings:

| Component | embraOS (Digital Ark) | FCA (a contested claim) |
|---|---|---|
| **States S** | Session states | Successive **public framings** of the claim — each a bounded interval during which one boundary condition is asserted to hold |
| **Alphabet Σ** | Input tokens, API calls | **Scrutiny events** `σ`: a debunking, an independent analysis, a demand to *show the data* or *decode the thing*, a failed replication |
| **Transition δ** | Request routing | The (would-be) move from one framing to the next — legitimate only under the **same** `ψ` |
| **Initial s₀** | First sealed soul document | The first public framing, asserting `ψ₀` |
| **Accepting F** | Valid session continuation | **Withdrawal / honest termination** — the claim conceding `ψ` failed. *Rarely reached; the pathology is precisely its avoidance.* |
| **Invariant ψ** | Soul-document verification | The boundary condition the claim asserts to hold its identity ("this is anomalous because ___") |
| **Verifier σ_verify** | Soul check at boot (retained) | The evaluation of `ψ` against reality — **retained as in DeepSeek**, but here it is the thing the claim is organized to keep from running |

**The crucial difference.** In embraOS `ψ` is checked at each boot; in QNM it is a *projection* (`P_ψ`); in
SOL a *conservation law*; in MWA *einselection*; in DeepSeek the *check itself, kept*. In the Diagnostic
Epoch `ψ` is **none of those — it is substituted**. When `σ_verify` would reject, the claim does not halt;
it asserts a *fresh* `ψ` under the *same label* and calls the result a continuation. The mechanism verb of
this family is therefore **substituted**, and its signature operation is `σ_subst` (legend §14). Where the
manifold derivations are interesting for how they *avoid having to check* `ψ`, and DeepSeek for how it
*actually checks* it, this one is interesting for how a claim *fakes the check having passed*.

## The core failure mode — ψ-substitution (`σ_subst`)

By the formal definition (`README.md` §3; legend §8), an epoch **halts** when its boundary condition fails
verification:

```
δ(s', σ) = s   ∧   ψ(s) = false     ⇒   halt (no valid successor)
```

A claim that respected its own invariant would terminate here (reach `F` — withdrawal). The observed
behavior is different: **it does not halt; it transitions, and asserts a continuity across the transition it
has not earned.** Formally, a framing's **public identity** is a pair `(L, ψ)` — a **label** `L` and the
**invariant** `ψ` it currently asserts. Healthy continuation by `δ` holds `ψ` fixed; the pathology, `σ_subst`,
holds `L` fixed while `ψ` changes after a rejection:

```
σ_subst(L, ψₙ, σ) = (L, ψₙ₊₁)     defined exactly where   σ_verify(s, ψₙ) = reject  ∧  ψₙ₊₁ ≠ ψₙ
```

`σ_subst` occupies the slot where the healthy automaton would halt. The Buga trajectory makes it concrete:

| Framing | Asserted `ψ` | `σ_verify` outcome | Response |
|---|---|---|---|
| `s₀` — "unexplained orb" | no welds · three layers · anomalous flight | **reject** — casting / superplastic forming clear the seam; a drone-on-wire clears the flight | does **not** halt |
| `s₁` — "ancient artifact" | 12,560-yr ¹⁴C date · alloy unknown to science | **reject** — the date measured organic residue, not the object; "ancient + industrially-refined aluminium" is self-canceling | does **not** halt |
| `s₂` — "suppressed disclosure" | the rejections are themselves the cover-up | — (see *The nesting layer*) | absorbed upward |

The identity violation is the crux. `s₁` is a *valid continuation* of `s₀` only if `δ(s₀, σ) = s₁ ∧ ψ(s₁) =
true` **under the same invariant**. What actually happens is that `ψ₀` is rejected, a *fresh* `ψ₁` is
asserted, and the prior label `L` = "the Buga sphere" is retained. That is not continuation. It is a **new
epoch wearing the previous epoch's name, claiming an identity it has not established** — the framework's
central commitment applies directly: *continuity is verified, not assumed.*

The DMT case shows the same move in a tighter loop — **ψ-substitution as retreat under pressure.** Pressed
on the objective claim ("is it really *code*; does it encode anything?"), the assertion swaps `ψ` from the
objective-substrate predicate — that the code is *out there in the ether* — to the private-experience
predicate — *try it yourself* — while keeping the label "the code." The two `ψ` are not the same predicate:
one is a claim about the world, the other a claim about a brain state. Retaining the name across the swap is
the identical unearned-continuation error, executed in a single conversation rather than over a year.

This yields the defining structural requirement:

> **`σ_verify` must never be allowed to run on the live `ψ`.** Each genuine evaluation kills the current
> invariant and forces a substitution. The claim survives only in the gap between assertions, never inside
> one.

## The taxonomy — atomic survival mechanisms

The trajectory view buys what the truth-value view cannot: it classifies *how a claim survives*,
orthogonally to whether it is true. Each atomic mode defeats a specific part of the verification machinery.

| Mode | Mechanism | What is defeated | Worked instance |
|---|---|---|---|
| **ψ-substitution** (`σ_subst`) | swap `ψ` when `σ_verify` rejects, keep the label | the identity predicate (continuity is faked) | Buga: orb → ancient → suppressed; DMT: object → experience |
| **ψ-vagueness** | never specify `ψ` sharply enough to be testable | `σ_verify` has no admissible input | "the code encodes a fundamental function of reality" |
| **σ_verify-capture** | only an interested party may run the predicate | the verification function itself | Buga (`cap_ext`); DMT "try it yourself" (`cap_int`) |
| **Nesting absorption** | leaf epoch dissolves; superstate `ψ` persists | propagation (rejection never reaches the root) | "NHI suppressed"; "reality is code" |

**`σ_verify`-capture has two flavors,** and the second case sharpens the distinction:

- **External capture (`cap_ext`)** — the test is possible in principle but **gatekept**. A party controls
  physical or social access so only they can run it. Buga is this: the object is held, the chain of custody
  is absent, the lab data unpublished. The remedy exists (demand independent custody and raw data); it is
  simply refused. **It is remediable.**
- **Intrinsic capture (`cap_int`)** — the test is excluded *by construction*, because the claim is about a
  private state. "You have to see it yourself" is not gatekeeping; it is a predicate only runnable from
  inside the experience. There is **no remedy** — you cannot demand custody of someone's percept. The DMT
  claim is the pure form, and the "try DMT" reply a research enquiry draws is the honest report of it: the
  verification function lives inside the experience, which is also a confession that nothing is verifiable
  from outside it.

Intrinsic capture is the more dangerous, because it has the *texture* of humility ("just go and look for
yourself") while being the strongest possible firewall around `ψ`.

## The testable-kernel seam — the derivation axis

The four modes above are atomic. The DMT case demonstrates the first **compositional** pattern, and it is
the structural variable this derivation is named for. A claim binds a substate with a *runnable* `σ_verify`
to a superstate that is `σ_verify`-captured, and survives by **laundering** the substate's credibility onto
the superstate. The seam splits the claim:

- **Testable kernel `ψ_k`.** Does a diffracted 650 nm laser produce a structured field the visual system
  resolves into character-like forms? This is *sober-testable, no drugs*. The neurobiologist Andrew
  Gallimore — who studies DMT — supplies the mechanism: a **laser speckle** effect (a granular field of
  dark/light retinal spots) acting as a "sensory scaffold" the altered brain completes into katakana-like
  glyphs. This sub-invariant has a real `ψ_k` and a runnable `σ_verify`. It may even be a real, minor
  perceptual effect.
- **Captured super-invariant `ψ_c`.** That this is *the* Code — objective, *out there*, encoding something.
  No message has been decoded, no information extracted, no content shown. "Code" is an unearned label on
  "characters."

The survival mechanism is the **credibility-laundering coefficient** `λ_seam ∈ [0,1]`: the degree to which
`σ_verify(ψ_k) = accept` is propagated to `ψ_c`. Legitimately `λ_seam = 0` — a sober speckle pass says
*nothing* about whether the characters encode anything. The pathology is `λ_seam > 0`: a casual challenge is
met with "but you can see the pattern *sober* — it's a real optical effect," which is true and entirely
beside the load-bearing claim. The clean substate launders the dirty superstate.

The diagnostic that falls out is reusable:

> A claim that *contains* a clean sober test is not thereby validated. Check whether the test actually bears
> on the **load-bearing predicate**. For DMT, the speckle test confirms *"a structured percept appears"* —
> it never confirms *"it encodes something."* The **decode** is the test that would matter, and it is the
> one that never runs.

A claim's trajectory is largely determined by **where the seam sits** (how much of the claim is `ψ_k` vs
`ψ_c`) and **how much credibility crosses it** (`λ_seam`). That is a single structural variable with
predictive content — the right shape for a named derivation in this project. Pressing the seam is what
triggers the retreat above: when the kernel's credibility is shown not to transfer (`λ_seam` forced toward
0), the claim falls back from "objective code" to "try it yourself" — from `cap_ext`-adjacent to `cap_int`.

### The consistency tell

Both cases lean, at their strongest, on **inter-observer consistency** — *everyone sees the same glyphs*;
*many independent witnesses report the same object*. This is the most persuasive-feeling evidence and the
most over-read. Consistency across observers is **predicted by the mundane model**, not evidence against it.
For DMT: identical optical input (same wavelength, same grating) + shared neural hardware (the same V1
form-constant architecture in every human) + a shared cultural prior (*The Matrix* installed the template
"code = falling green katakana" in essentially everyone) → convergent percepts, **no external substrate
required**. *Same input + same brain + same prior = same hallucination.* There is direct precedent:
character-shaped hallucinations are a recognized content type in Charles-Bonnet syndrome, and the text they
produce is characteristically **unreadable — "from no known language," nonsensical on inspection** — which
is exactly the DMT "code" that parses to nothing.

The rule: **shared ≠ external.** Convergence is what the boring model predicts; treating it as the signature
of a shared realm is the error. (And the claimed consistency is usually weaker than advertised — reports
range from a single "source code" to a whirl through thousands of distinct scripts. *Why just one, anyway?*)

## The nesting layer — two pathologies

Both cases exhibit hierarchical structure (`README.md` §3 nesting): a superstate persists while its
interior substates transition. But they fail the nesting layer *differently*, and the contrast is itself a
result.

**Pathology A — absorption of rejection (Buga).** The **"Buga-is-alien"** sub-automaton can terminate
completely — every leaf claim rejected — while the superstate **"non-human intelligence is real and
suppressed"** persists untouched, because the superstate's own `ψ` is constructed to be unfalsifiable.
Worse, under a suppression narrative a *thorough* leaf rejection appears to **confirm** the superstate: the
more decisively a substate is debunked, the more the debunking reads as evidence of the suppression.
Rejection is ingested as corroboration.

**Pathology B — legitimation by kernel (DMT).** The **"reality is code"** superstate is not propped up by
false-confirmation but by a *true* leaf — the speckle effect is genuinely there. Here the danger is the
inverse of Pathology A: a real sub-truth is borrowed to underwrite a super-falsehood (`λ_seam > 0`). The
superstate survives not because rejection feeds it, but because one of its substates passes a real test and
the pass is allowed to bleed upward.

Both obey the same formal constraint, and that is the point:

```
ψ(superstate) invariant across all interior transitions
   ⇒  the fate of any sub-epoch cannot, on its own, reach the root
```

Leaf termination does not reach the trunk; neither does leaf *success* legitimately climb it. An observer
who watches only the substate sees the claim die (Buga) or sees it "proven" (DMT); an observer who watches
the superstate sees it untouched either way. **Tracking the invariant rather than the substate is the whole
method.**

## Formal Definition: The FCA Automaton

Instantiating the Epoch Automaton 6-tuple directly over the discrete space of a claim's public framings.
Like DeepSeek, it does **not** rename the state space — it **reuses** the §1 glyphs and adds the operators
that describe evasion:

```
FCA = (S, Σ, δ, s₀, F, ψ)
```

| Symbol | Meaning |
|---|---|
| **S** | Successive public framings of one claim; each `s ∈ S` is a bounded interval during which one `ψ` is asserted |
| **Σ** | Scrutiny events `σ`: debunking, independent analysis, demand to show data / decode, failed replication |
| **δ: S × Σ → S** | The (would-be) transition between framings — a *valid* continuation only under the same `ψ` |
| **s₀** | The first public framing, asserting `ψ₀` |
| **F** ⊆ S | Withdrawal / honest termination (`ψ` conceded false) — rarely reached; the pathology is its avoidance |
| **ψ: S → {true, false}** | The boundary condition the claim asserts to hold its identity |
| **`(L, ψ)`** | A framing's public identity: label `L` (held constant to fake continuity) + asserted invariant `ψ` |
| **`σ_subst`** | The substitution pseudo-operation — the un-earned continuation that occupies the halt slot |
| **`ψ_k` / `ψ_c`** | Testable-kernel sub-invariant (runnable `σ_verify`) / captured super-invariant (no admissible `σ_verify`) |
| **`λ_seam` ∈ [0,1]** | Credibility-laundering coefficient across the seam; legitimate 0, pathology > 0 |
| **`cap_ext` / `cap_int`** | External (gatekept, remediable) / intrinsic (private-state, irremediable) `σ_verify`-capture |
| **`⊢₀ (ψ, σ_verify)`** | Prospective-commitment condition: `ψ` and its test are declared at `s₀`, before any dissolution (anti-tautology, below) |

**Key property (boundary-native via *evasion*, not verification):**

`σ_verify` (the Ark's verification function, legend §2) is **retained** as in DeepSeek — but the FCA is the
automaton organized to keep it from running on the live `ψ`. The defining condition is the negation of
DeepSeek's:

```
δ(s, σ) = s'   would be a valid continuation   iff   ψ(s') = true under the SAME ψ
                                               but   σ_verify(s, ψ) = reject   ⇒   σ_subst fires (halt is evaded)
```

Unlike the manifold derivations, nothing keeps the system inside the valid region — and unlike DeepSeek,
nothing makes it halt honestly. A rejection that *should* terminate the epoch is instead absorbed by a
substitution. The boundary is neither maintained (QNM/SOL/MWA) nor honestly checked (DeepSeek): it is
**faked**, and the apparatus exists to read the fake off the record.

### The FCA State-Machine

The same state-machine, expressed for a claim under scrutiny. Where DeepSeek's Ark seals `ψ` and *honestly
refuses* a transformation that crosses `τ`, here the Ark is the **analyst** who seals `(ψ, σ_verify)`
*prospectively* (`⊢₀`) and then *watches* — and the claim, on rejection, **substitutes** rather than halts.
It is forward-directed, exactly as the core state-machine is; the retrocausal `δ*` is deliberately absent.

```
                 ┌─────────────────────────────────────────────────┐
                 │        THE ARK  (analyst / framework-applier)   │
                 │  commits (ψ, σ_verify) prospectively at s₀ (⊢₀);│
                 │  names the test that WOULD reject, before drift │
                 └────────────────────────┬────────────────────────┘
                                          │ σ_verify(s, ψ) = REJECT
                                          ▼
   ┌──────────────┐ σ_subst  ┌──────────────┐ σ_subst  ┌──────────────┐
   │ FRAMING s₀   │────────▶ │ FRAMING s₁   │────────▶ │ FRAMING s₂   │
   │ "orb"        │ un-earned│ "ancient"    │ un-earned│ "suppressed" │
   │ ψ₀           │  (≠halt) │ ψ₁ ≠ ψ₀      │  (≠halt) │ ψ₂ ≠ ψ₁      │
   └──────────────┘          └──────────────┘          └──────────────┘
        label L = "the Buga sphere" — held CONSTANT across every swap
   · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · · ·
   healthy automaton HALTS here (ψ = false). FCA does not: σ_subst asserts
   a fresh ψ under the same label L — a replica wearing one name.
   seam:  ψ_k (kernel, σ_verify runs) ──λ_seam──▶ ψ_c (captured, no test)
   ┌─────────────────────────────────────────────────────────────────────┐
   │ MEMORY / RECORD  M  —  append-only public trajectory                │
   │ [(s₀,σ,reject,subst), (s₁,σ,reject,subst), …]  the replica chain    │
   │ the endpoint hides; the substrate for ψ↑_scrutiny                   │
   └─────────────────────────────────────────────────────────────────────┘
                                          ▲
                                          │ queries (read-only)
                                  ┌───────┴───────────┐
                                  │ THE STEWARD       │
                                  │ skeptic / auditor │
                                  │ ∉ S; replays M,   │
                                  │ re-runs σ_verify, │
                                  │ reads the verdict │
                                  └───────────────────┘
```

The verification gate is **present** (as in DeepSeek, against QNM/SOL/MWA) — but its verdict is *evaded*,
not honored. The Ark and Steward are **inverted** from the operational case: the Ark is not the claim's
custodian but the analyst who seals the predicate before watching; the Steward is the external skeptic who
replays the record and reads the verdict the trajectory already wrote.

**Discrete state-machine ↔ FCA, element by element:**

| Discrete Epoch Automaton `E` | FCA Automaton | Note |
|---|---|---|
| state `s ∈ S` | a public framing (label + asserted `ψ`) | the §1 state, made concrete |
| transition `δ(sᵢ, σⱼ)` | the move between framings under scrutiny | valid only under the **same** `ψ` |
| verification step (`σ_verify`) | **retained** — but the claim is built to evade it | contrast DeepSeek, where it is honored |
| halt when `ψ(s) = false` | **`σ_subst`** fires instead — the un-earned continuation | the defining pathology |
| initial epoch `s₀` | the first framing, asserting `ψ₀` | genesis |
| terminal set `F ⊆ S` | withdrawal / honest termination | rarely reached — avoidance is the pathology |
| nested epoch `(S_sub, …, ψ_sub)` | leaf claim under an unfalsifiable superstate | the two nesting pathologies above |
| Memory `M = [(s₀,σ₁,s₁), …]` | the **public** record of framing · scrutiny · outcome · substitution | a literal, externally-auditable log |
| Steward (oracle, `∉ S`) | the external skeptic / community auditor | **literal**; replays `M`, re-runs `σ_verify`; cannot drive `δ` |

> Note — `ψ` here is still **pointwise** (`ψ: S → {true, false}`): each framing's `ψ` is checked at a point.
> What makes the *fraud* visible is not a richer pointwise `ψ` but the **trajectory** in `M`. A
> trajectory-valued `ψ↑_scrutiny` over that record — one that flags a substitution (`ψₙ₊₁ ≠ ψₙ` after a
> reject) — would **pass the replica test by construction**: it calls a substitution-chain "died and
> replaced" and a genuinely-stable claim "survived." That is the vertical-/horizontal-lineage hand-hold
> the project already names for DeepSeek (transformation-lineage), MWA (decoherence-record), and the Void
> (genealogy-lineage `ψ↑`) — here, a **scrutiny-lineage**. A **direction**, not a result (see *Open
> problems*).

**Operational reading** (the analyst's loop — a genuine detector):

```
Commit       ⊢₀ : seal (ψ, σ_verify) at s₀, prospectively — name the test that would reject
Watch        on each scrutiny event σ, run σ_verify(s, ψ)
Reject       σ_verify = reject  →  the healthy successor is HALT (reach F: withdrawal)
Substitute   the claim instead fires σ_subst(L, ψₙ, σ) = (L, ψₙ₊₁) — a new ψ under the same label
Read         the Steward replays M; a substitution after a reject is the recorded verdict
```

**The Steward, in diagnostic terms** — the same external oracle as the core machine (`Steward ∉ S`), and
here **literal**: the independent investigator / scrutinizing community that replays the public record and
re-runs `σ_verify`, but cannot drive the claim's `δ`.

```
Steward ∉ S
Steward may query:   the public record M = [(s₀,σ,outcome,subst), …],  ψ,  σ_verify
Steward may not:     drive δ  (cannot force the claimant's next framing)
```

*Mapping, not endorsement. This figure illustrates a method you actually run against the public record of a
claim: commit the predicate, watch, read the substitutions. Its **formal apparatus** (`σ_subst`, the seam
`λ_seam`, the capture predicates, `⊢₀`) is drafted; its **validation** — scoring `λ_seam` and seam-position
against a corpus of claims to test the predictive reading — is the pending work in the Current Status table.
It is forward-directed by design; the speculative `δ*` is deliberately not part of it.*

## The anti-tautology discipline (load-bearing) — `⊢₀`

The same blade the project takes to its own speculative material must be turned on this analysis, or it is
worthless. **Everything above is true by construction unless `ψ` and `σ_verify` are committed
*prospectively*.** If `ψ` is permitted to be defined as "whatever held the claim together until it broke,"
then *every* belief trivially exhibits epoch structure, and the framework has explained nothing — it has
relabeled "people believed it until they didn't" in Greek letters. Retrodictive `ψ` is not an analysis; it
is a tautology with notation.

The earning condition `⊢₀` is strict. Standing at `s₀`, before any dissolution, one must be able to (1)
**state the boundary condition** `ψ` the claim relies on, and (2) **name the test** `σ_verify` that would
evaluate it, such that the automaton flags the epoch as **unstable before it dissolves**. Both cases meet
the condition, by different signals:

- **Buga.** At the orb stage — before the metallurgy, before the dating — `ψ` was already walled off from
  `σ_verify`: no chain of custody, no published data, a promoter-controlled object (`cap_ext`). A
  prospective instability signal, readable at `s₀`.
- **DMT.** At the outset, the *seam* was already visible: the "encodes something" predicate `ψ_c` had **no
  admissible `σ_verify`** (no message ever extracted, none proposed), while the speckle predicate `ψ_k`
  did. The case was flagged as kernel-laundering before the superclaim's failure, not after.

This is the discipline the project runs on everywhere else: **fix the predicate first, then watch.** With
it, the trajectory view is a forward-looking instability detector; without it, it is tautology. The
difference is the entire value of the method — and the reason `⊢₀` is registered as a well-formedness
condition, not a flourish.

## Methodological note — do not reach for `δ*`

One trap is worth marking explicitly, because it is the project's *own* scaffolding and is therefore
tempting. There is a seductive reading in which a late "confirmation" sends a handshake *backward* across
the boundary to legitimize the original intuition — the future state validating the past, i.e. the
retrocausal `δ*` handshake (`README.md` §4; legend §3). Both cases offer the bait:

- **Buga.** The eventual lab-flavored report, the conference, the dating — read as the future certifying
  that the orb "was always" an ancient artifact.
- **DMT.** *"I saw it, therefore it was always out there in the ether"* — the experience retroactively
  certifying an objective substrate the vision is then said to have merely *revealed*.

**Resist both.** This is the *appearance* of the handshake without the mechanism. `δ*` is already designated
non-load-bearing in the core framework — there is no mechanism for it in forward autoregressive inference,
and none in forward belief formation either. The backward-legitimation observed here is ordinary motivated
reasoning (pattern-completion + cultural prior + interpretive commitment), and it is **fully explained by
the forward direction alone**. Importing `δ*` to describe it would dress a forward-explicable phenomenon in
the project's most speculative element — precisely the move this project flags when it appears in others'
work. The forward `σ_subst` is the whole mechanism; nothing travels back.

## Load-bearing vs scaffolding

Instantiating the framework against real claims forces a sorting: which elements do *detection* against the
record, and which are *framing* with no mechanism underneath.

| Framework element (source) | Verdict | Realization on the two cases |
|---|---|---|
| `σ_subst` — substitution detection (the halt that didn't happen) | **Load-bearing** | Buga's orb→ancient→suppressed; DMT's object→experience — read off the record |
| The testable-kernel seam — `ψ_k` / `ψ_c` / `λ_seam` | **Load-bearing** | DMT's speckle (`ψ_k`) laundered onto "the Code" (`ψ_c`); the predictive variable |
| `cap_ext` / `cap_int` — capture taxonomy | **Load-bearing** | Buga (held object, unpublished data) vs DMT ("try it yourself") |
| `⊢₀` — prospective commitment | **Load-bearing** | the anti-tautology gate; both cases flagged unstable at `s₀` |
| The Ark / Steward — inverted (analyst / skeptic) | **Load-bearing** | a literal external auditor replaying a public record |
| `ψ↑_scrutiny` — scrutiny-lineage trajectory-`ψ` | **Load-bearing, speculative** | the direction toward the replica test; not built here |
| `δ*` — retrocausal handshake | **Scaffolding** | no mechanism; backward-legitimation is forward motivated reasoning |
| Cosmological / "deeper realm" framing of either claim | **Scaffolding** | the claims' own motivating register — not a mechanism |

The two scaffolding rows are fenced exactly as `README.md` §4 fences them: `δ*` is conceptual framing for
boundary *negotiation* only (the sound version is the distributed-commit reframe), and the "deeper realm"
register belongs to the claims under study, not to the method.

## Connection to the two cases (the real grounding)

The method is only honest if the factual anchors are real. Both cases are documented against the public
record below; **contested or thinly-sourced items are fenced, not asserted.**

**The Buga Sphere (Colombia, 2025–26).** A metallic orb filmed in erratic flight and recovered near Buga on
2 March 2025; the promotion chain runs finder José Arias Restrepo → cousin David Vélez ("El Potro," who
sells metal detectors) → ufologist Jaime Maussan, with Steven Greer also promoting. The escalation `s₀ →
s₁ → s₂` is on the public record: "anomalous orb" → "~12,560-year-old artifact of an alloy unknown to
science" → "suppressed non-human intelligence." The refutations:

- **Metallurgy.** Reported composition ~95% aluminium; a seamless, weld-free orb is readily produced by
  ordinary casting / 3D-printing / superplastic forming. "No welds ⇒ extraterrestrial" is a non-sequitur.
- **Dating.** ¹⁴C dates *organic* material, not metal; at best the date is of residue, not the object.
  Metabunk's dissection of the report notes it references *foraminifera* with a δ¹³C (≈ −28.6‰) wrong for
  marine microfossils, plus outdated standards — "appears to be a fabrication." And aluminium was not
  industrially refined until ~1876, so "ancient + industrially-refined alloy" is self-canceling.
- **Provenance (`cap_ext`).** Promoter-controlled throughout; no chain of custody; no peer-reviewed
  analysis; no confirmation from the named dating lab.

> **Caution (fenced).** A widely-circulated report has Maussan stating on his program *No Humano* (~10 May
> 2026) that the sphere was **"cut open and resealed before reaching the investigation team"** and that
> authenticity cannot be confirmed — a striking real-time confession of `cap_ext` (custody collapse). This
> is **sourced to second-hand summaries and not independently verified against a primary recording**; it is
> cited as illustrative, not load-bearing. Treat the "ancient + industrial alloy," "no welds ⇒ alien," and
> "elements unknown to science" claims as discredited-by-inference, the precise provenance details as
> contested, and the tampering admission as needs-primary-verification.

**The "Code of Reality" (DMT-laser, 2020–present).** Originated by Danny Goler (~Aug 2020); a glyph
"registry" and "validation" claims circulate via codeofreality.com / dmtcode.com. The seam:

- **Kernel `ψ_k` (real).** Laser speckle is textbook coherent-light optics — a granular interference field
  on the retina, *more* prominent for red (650 nm). Gallimore attributes the percept to speckle as a stable
  "sensory scaffold" the DMT-altered brain completes into glyphs (cf. Klüver form constants). *Cite him for
  the mechanism, not as a hostile debunker — his own work entertains a "reality-as-information" cosmology;
  he nonetheless rejects the objective-external-code reading and notes no message has been decoded.*
- **Captured super-invariant `ψ_c` (untested).** "It is *the Code*, encoding reality." The **decode** — the
  one test that bears on `ψ_c` — has **never been run** across every source examined (Goler's own pilot, the
  registry, the critical coverage). The load-bearing predicate is the test that never happens.
- **Cultural prior.** *The Matrix*'s "digital rain" (reversed Roman + katakana, sourced from a sushi
  cookbook) installed a shared "code = green katakana" template; convergence on katakana specifically is a
  priming signature, not an external substrate. Cultural priors are known to shape hallucination content.
- **Character-percept precedent.** Charles-Bonnet syndrome produces text/letter hallucinations as a
  recognized content type, characteristically **unreadable / "no known language"** — mirroring a "code"
  that parses to nothing. *(The earlier draft's "~25% of CBS cases involve text" figure is **withdrawn** —
  unverified against a primary source; the qualitative "recognized, typically-unreadable subtype" is the
  defensible — and stronger — statement.)*

> **A clean instance of a manufactured `σ_verify`.** dmtcode.com bolsters its claims with *"Davis et al.
> 2021, DOI 10.1002/hup.2806, 87% reporting consistent symbols."* That DOI resolves to an **unrelated
> paper** — a *zuranolone (SAGE-217) phase-1 insomnia study* in *Human Psychopharmacology* — with nothing
> to do with DMT, lasers, or glyphs. A fabricated citation is `σ_verify`-capture in its purest form: the
> *appearance* of a passed external test, with no test behind it. (Checkable; flagged as a positive
> fact-check finding.)

## Open problems (inherited, not resolved)

None is solved here; each is flagged in the spirit of `README.md` §6.

- **`ψ` is still pointwise.** The fraud is visible in the **trajectory** (`M`), not in any single framing's
  `ψ`. A formal `ψ↑_scrutiny` over the record that provably passes the replica test is **not supplied** —
  it is named as the natural next step (the scrutiny-lineage hand-hold), a *direction* like DeepSeek's and
  MWA's, not a result. `EPOCH-DEFINING-THE-INVARIANT.md` is the bar it would have to clear.
- **`λ_seam` is proposed, not validated.** The claim that seam-position + `λ_seam` *predict* a claim's
  trajectory is a hypothesis. It needs scoring against a corpus of claims (true, false, and mixed-kernel)
  before it earns "predictive." Until then it is a sharp re-description, not a measurement.
- **The mode taxonomy's completeness is unproven.** Four atomic modes + one compositional pattern + two
  nesting pathologies are *observed*, not shown exhaustive. A third case could surface a fifth mode.
- **Intrinsic capture has no remedy — by design.** `cap_int` is a genuine limit of the method, not a bug:
  for a purely private-state claim there is no external `σ_verify` to run. The method can *name* the
  capture; it cannot dissolve it.

**Acceptance-bar verdict (named, per `EPOCH-DEFINING-THE-INVARIANT.md`).** This derivation is a **valid
re-description that yields a novel diagnostic with a predictive variable** (the testable-kernel seam,
`λ_seam`), plus an **empirical instance of the replica-test failure** (ψ-substitution as a replica chain
wearing one label). It does **not** resolve the dynamic-`ψ` problem; it engages it as a *direction*. It sits
firmly on the **schema** side of the schema-vs-theory-of-everything fork: `ψ` is "whatever the claim staked
its identity on," instantiated differently per claim — a tool, not a universal `ψ` beneath all claims.

## Current Status

| Phase | Status |
|---|---|
| **Theoretical foundation** | ✅ Established — Epoch Automaton formalism (2026) |
| **The objects** | ✅ Real & publicly documented — Buga Sphere (2025–26) and the DMT "Code of Reality" (2020–) |
| **Formal mapping** | ✅ Drafted — the `FCA = (S, Σ, δ, s₀, F, ψ)` instantiation + `σ_subst` / seam / capture / `⊢₀` (this document) |
| **Diagnostic validation** | ⬜ Pending — scoring `λ_seam` and seam-position against a corpus to test the predictive reading; attempting `ψ↑_scrutiny` against the replica test |

## References

Sourced against the public record (2026-06-19). Reputable / specialist sources are marked; fringe-promoter
and second-hand sources are flagged and used only as primary *artifacts of the claim*, not as evidence.

- `README.md` — formal Epoch definition and the §4 fenced motivating metaphors (`δ*`)
- `EPOCH-NOTATION-LEGEND.md` §14 — the FCA notation registered for this derivation
- `EPOCH-DEFINING-THE-INVARIANT.md` — the replica test and the dynamic-`ψ` open problem this derivation
  engages
- `Discrete_Derivations/DeepSeek-V4-Pro_Epoch-Formula.md` — the operational discrete derivation this one
  mirrors (ψ *held* vs ψ *evaded*)

*Buga Sphere —*
- El País (Colombia), *"El misterio de la esfera de Buga… ¿ovni o montaje según científicos?"* — named
  Colombian scientists, provenance chain. `https://www.elpais.com.co/tecnologia/el-misterio-de-la-esfera-de-buga-que-termino-en-manos-de-jaime-maussan-ovni-o-montaje-segun-cientificos-1241.html`
- Infobae, *"La esfera de Buga: ¿misterio ancestral o fraude moderno?"* (17 Oct 2025) — escalation,
  marketing-stunt hypothesis. `https://www.infobae.com/espana/2025/10/17/la-esfera-de-buga-misterio-ancestral-o-fraude-moderno-un-supuesto-artefacto-de-12560-anos-de-antiguedad-que-levita-y-emite-campos-electromagneticos/`
- Metabunk, *"Buga Sphere carbon dating"* — technical dissection of the dating report (foraminifera / δ¹³C
  inconsistencies; contamination). Forum, document-based. `https://www.metabunk.org/threads/buga-sphere-carbon-dating.14454/`
- The Jerusalem Post (27 May 2025) — careful claim/fact separation. `https://www.jpost.com/science/science-around-the-world/article-855587`
- *(Fenced)* The ~10 May 2026 *No Humano* "cut open and resealed" remark — second-hand summaries only; not
  independently verified.

*Code of Reality (DMT-laser) —*
- Vice, *"The Man Who Thinks He Found the Source Code of Reality on DMT"* (28 Jan 2025) — skeptical
  coverage; the not-universal critique. `https://www.vice.com/en/article/danny-goler-dmt-vape-laser-simulation/`
- A. Gallimore, *"On the DMT laser 'Code of Reality' effect"* (21 Jan 2025) — the laser-speckle "sensory
  scaffold" mechanism; rejects the objective-code reading. `https://alieninsect.substack.com/p/on-the-dmt-laser-code-of-reality`
- E. Prideaux, *"Cracking the Code"*, Ecstatic Integration (27 Dec 2024) — investigative; the *Matrix*
  priming argument. `https://www.ecstaticintegration.org/p/cracking-the-code`
- *(Primary artifact of the claim)* dmtcode.com — the glyph registry and the misattributed
  *"Davis et al. 2021, DOI 10.1002/hup.2806"* citation (resolves to an unrelated zuranolone insomnia study
  in *Human Psychopharmacology*). `https://dmtcode.com/`
- Teunisse et al., *"Visual hallucinations in psychologically normal people: Charles Bonnet's syndrome,"*
  *The Lancet* 347 (1996) — CBS prevalence and content. `https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(96)90869-7/fulltext`
- Snopes, *"Is the Code in 'The Matrix' Sushi Recipes?"* — the katakana template. `https://www.snopes.com/fact-check/the-matrix-code-sushi/`

---

*A claim that has to keep changing what holds it together has already reported its own result: the invariant
does not hold. The trajectory is just the time it takes for everyone else to read the verdict — and, where
the claim hides a real test in front of a fake one, the time it takes to notice which test was ever being
run.*
