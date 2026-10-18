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
- `consensus` provides reusable consensus algorithms and disagreement-handling behavior.
- `evaluation` determines whether a result satisfies an intended outcome.
- `model-gateway` owns provider-neutral model invocation and resource management.

Consensus must not bypass authorization, policy, safety, or budget constraints. It should expose enough evidence to explain how an aggregate result was produced.
