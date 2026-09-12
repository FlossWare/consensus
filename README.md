# consensus-ai

**Reusable consensus and disagreement strategies for FlossWare.**

Consensus is a strategy/capability that can be used by a Loom Worker, Arbiter, evaluator, or another compatible runtime. It is not the Arbiter abstraction itself.

## Boundary

```text
Worker / Arbiter / Evaluator
          │
          ▼
   Consensus Strategy
    ├── majority vote
    ├── weighted consensus
    ├── quality threshold
    └── disagreement detection
```

Loom owns orchestration. `consensus-ai` owns reusable consensus behavior.

Consensus must not become another model-routing or orchestration framework. Model invocation belongs to `model-gateway`; execution composition belongs to `loom-ai`; authoritative evaluation belongs to the evaluation contract.

## Strategies

Current implementations include majority voting, weighted consensus, quality thresholds, disagreement detection, and reusable fan-out/cascade helpers where those helpers remain useful as standalone strategies.

## Migration

The package previously described itself as an LLM orchestration/execution-pattern library. The architectural boundary is now narrower: preserve reusable consensus behavior and move orchestration concerns into Loom.

## License

MIT
