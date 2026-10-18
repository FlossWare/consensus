# consensus

**Reusable consensus and disagreement-handling capability for FlossWare.**

This repository provides reusable consensus behavior for a Loom Worker, Arbiter, evaluator, or another compatible runtime. It is not the Arbiter abstraction itself and does not own orchestration.

## Boundary

```text
Worker / Arbiter / Evaluator
          |
          v
       consensus
          |
          +-- majority and weighted aggregation
          +-- quality thresholds
          +-- disagreement detection
          +-- consensus evidence
```

## Responsibility split

- `loom-ai` defines AI-domain execution contracts and semantics, including Worker and Arbiter behavior.
- `consensus` should own reusable consensus algorithms and disagreement-handling behavior.
- `evaluation` determines whether a result satisfies an intended outcome.
- `model-gateway` owns provider-neutral model invocation and resource management.

**Implementation mismatch to resolve:** the current `consensus_ai` package also exports `ConsensusPattern`, `CascadePattern`, `MapReducePattern`, `with_cascade`, and a `ModelRouter` protocol. These are real current APIs, but generic workflow composition and model routing exceed the intended consensus boundary. Treat them as legacy surface pending a reviewed migration; this README does not imply they have already been removed.

Consensus must not bypass authorization, policy, safety, or budget constraints. It should expose enough evidence to explain how an aggregate result was produced.

## Packaging note

The repository is named `consensus`. The current distribution/import identifiers remain `consensus-ai` and `consensus_ai`; repository naming does not automatically rename a published package or Python imports. Change those identifiers only through an explicit compatibility and release decision.
