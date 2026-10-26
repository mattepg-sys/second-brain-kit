# Flows

One folder per flow, created when the flow is built (see `_guide/build-cycle/`).

```
<flow-name>/
├── card.md       # the design (flow card)
├── SKILL.md      # the runbook: purpose, inputs, context to read, steps, rules, output, checks
├── memory.md     # what this flow learned: "Accepted" lessons and "Proposed" ones awaiting approval
├── examples/     # good and bad past outputs
└── tests/        # sample inputs and what a correct result looks like
```

Every flow here must also appear in `_system/flows.md`.
