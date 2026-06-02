# Defining the Invariant — An Open Problem

*The central open problem of the Epoch framework, stated so that anyone can work on it — and so
that a real answer can be told apart from a fake one. The framework is meant to **pass or fail**;
the invariant ψ is where that happens. Contributions are welcome from any field. The price of
either breaking an application or confirming that it yields true insight is the time and energy
someone is willing to put into the proof.*

---

<p align="center">
  <img src="assets/epoch-invariant.png" alt="A Speculative Definition of ψ — the static form ψ: S → {true, false} (pointwise; folds into the state set, a name not a constraint) versus the speculative move ψ: Runs(S) → {true, false} (defined over whole trajectories; cannot be folded away if it survives the test). The discriminating (replica) test: two runs reach the same final state by different paths — one in which the thing survived with unbroken identity, and one in which the original died and was replaced by an identical copy; a static endpoint-only ψ calls them the same and is blind to the difference, while a trajectory ψ calls them different and tells survival from replica. The bar: a definition that cannot be false somewhere is a name; a definition that survives the replica test is a tool." width="100%">
</p>

## What ψ is, and why it is the crux

Across every derivation, ψ is the only element of the automaton `E = (S, Σ, δ, s₀, F, ψ)` that is
**load-bearing by claim but not yet load-bearing in fact.** `S, Σ, δ, s₀, F` are the standard
automaton furniture, re-labeled per substrate — and that is honest. ψ is the one claimed to be
the *soul* of the thing.

But as a **static, pointwise predicate** `ψ: S → {true, false}`, ψ folds into the construction:
restrict the state set to where ψ holds, or make the transition function partial, and you recover
an equivalent machine with no ψ at all. It adds a name, not a constraint.

So the framework currently rests on a placeholder. **Until ψ is defined as something that cannot
be absorbed, there is nothing here that can be proven or disproven — only re-described.** Defining
ψ is therefore not preliminary theory-work. It is the whole game.

## One form, several answers — schema, or theory-of-everything?

Each derivation uses a *different* ψ: binding (`E < 0`), decoherence / einselection,
projection-membership (`P_ψ`), verification (`σ_verify`). What they share is not a value but a
**form** — in every case ψ is *what is preserved-or-selected under the flow such that identity
survives.*

There is a fork here, and the project should be explicit about which side it claims:

- **One true ψ beneath them all** → a theory of everything. Elegant, and unfalsifiable.
- **A schema** → "ψ is whatever the dynamics leave fixed that constitutes a thing's continuity,"
  instantiated differently in each substrate. A definition, and usable.

The pull toward treating the collection as a single whole is real and worth following — but it
can lead to either of these. The first explains everything and predicts nothing; the second is a
tool. **Name which one is being claimed**, because the rest of the work depends on the answer.

## The discriminating test

A candidate ψ is only doing work if it can **distinguish trajectories that the pointwise version
cannot.** The test is substrate-independent:

> Take two runs that reach the **same final state** by **different paths** — one in which the
> thing *survived*, and one in which it *died and was replaced by an identical copy.*

A pointwise ψ sees only the endpoint and calls them the same. A genuine continuity-invariant
**must call them different.**

> If a candidate ψ cannot tell the Ship of Theseus from its replica, it is still the static
> predicate wearing a trajectory costume.

Run every proposed definition against this case first.

## The trap: true-by-construction

The characteristic failure of invariant-hunting is writing ψ so that it is **automatically
satisfied** — defining "the soul persists" as "the thing that persists." That is a tautology. It
explains nothing and forbids nothing.

A real ψ must be the kind of thing that **can be false mid-trajectory**, not only at a clean
boundary. Boundary-only invariants are too cheap; the content lives in the path.

## Where to look: history-laden identity

A trajectory-dependent ψ is most likely to be *found* wherever identity is genuinely
**history-laden** — where "the same thing" depends on the record laid down along the way, not
just on the present state.

Decoherence is the clearest natural example: whether a branch is "the same world" depends on the
decoherence record accumulated along its history, not on an instantaneous snapshot. That makes it
a good place to **discover the form** of a trajectory-dependent ψ — which can then be carried into
substrates where it can be *built*.

## Why constructed instances matter more than descriptions

There are two kinds of derivation, with very different relationships to failure:

- **Re-descriptions** map the framework onto systems that *already run* — orbital mechanics, the
  universal wavefunction. They are valuable for intuition, but **they cannot fail**: the system
  works whether or not the Epoch reading is apt. Re-describing a known truth in new vocabulary
  exposes no new claim to refutation.
- **Constructed instances** are systems *built* so that their dynamics are meant to hold ψ. These
  **can fail** — concretely and observably. A trainable model confined to a ψ-invariant manifold
  — a *constrained-manifold model* — is one example: it either trains within the constraint and
  stays on it, or it does not. Any substrate where ψ is *engineered rather than observed* is a
  candidate.

The falsification frontier therefore lives in two places: **a formal, trajectory-dependent ψ**,
and **any constructed system whose flow is meant to preserve it.** Both can yield a clear verdict.
The re-descriptions, on their own, cannot.

## What would count as progress

A real result moves the problem in one of these directions. All are welcome — including the
negative ones:

- A **formal, trajectory-dependent ψ** that provably expresses something the pointwise version
  cannot (i.e., that passes the replica test).
- A **proof that every such ψ collapses** back to a static predicate or a standard construct.
  This would be the framework failing honestly, and it is a fully legitimate outcome.
- A **constructed instance** — e.g., a constrained-manifold model — that demonstrably holds ψ
  along its trajectory, or demonstrably cannot.
- A **domain expert's verdict** on whether a specific derivation yields a *novel* insight or
  prediction, versus being a valid re-description with no new content.

> **"Valid re-description, no new predictions" is a real and expected verdict** — distinct from
> both "confirmed" and "broken." For the re-description derivations it may even be the *likely*
> verdict, and that is not a defeat: naming it honestly, derivation by derivation, is itself
> progress and keeps the framework from mistaking elegance for evidence.

## The bar

Two sentences — the acceptance criterion for any candidate ψ:

- **A definition that cannot be false somewhere is a name.**
- **A definition that survives the replica test is a tool.**

---

*The order of work that follows: define the invariant (schema or singular — say which), test each
candidate against the replica case, then build — because a constructed instance needs ψ as its
target. Refutations, collapses, and "this is only re-description" verdicts are as valuable as
confirmations. Each is paid for in the effort of the proof.*
