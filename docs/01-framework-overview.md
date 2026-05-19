# Framework Overview

Judgement-First Testing organises quality work across three layers and assigns each one a delegation rule:

| Layer | Focus | Delegate to AI? |
|-------|-------|-----------------|
| **Technical** | Correctness, performance, reliability of the system | Yes, aggressively |
| **Human** | Usability, accessibility, real user experience | With a human in the loop |
| **Strategic** | Risk, business value, long-term consequences | No |

The layers are independent concerns, not stages. Work happens across all three in parallel, with a human responsible for synthesising the result into a decision.

## The delegation rule, in one sentence

> Delegate execution. Keep judgement.

If a task is *what the system does*, an agent can probably do it faster than you. If a task is *what it means*, it stays with a human.

## How to read the rest of these docs

Each layer has its own page covering what it includes, what to delegate, common failure modes, and questions to ask in refinement:

- [Technical Layer](02-technical.md) — what to delegate aggressively to agents, and where the synthesis step still matters.
- [Human Layer](03-human.md) — where a tester stays in the loop, and why a green test suite isn't enough.
- [Strategic Layer](04-strategic.md) — what no agent can own, and how to surface it.

Then see the framework applied to real-shaped tickets:

- [Case Studies](examples/case-studies.md) — one worked example per layer focus, each ending in the decision that actually shipped.

## When in doubt

If you can't decide which layer a task belongs to, ask: *who carries the consequence if this is wrong?* That's the layer.
