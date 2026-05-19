# Technical Layer

*What the system does.*

Covers unit, integration, system, performance, and security testing — anything that can be verified against a specification.

## Goals
- Verify functional correctness
- Validate non-functional requirements (load, latency, security)
- Prevent regressions

## Delegation
**Largely delegable to AI agents.** Test generation, automation scaffolding, regression sweeps, and coverage analysis all benefit from agent speed. Humans verify direction, not every artefact.

---

## What good looks like

- The agent produces the test plan, the cases, and the automation — fast.
- A human spends their time on the **edges the spec didn't mention**: clock skew, partial failure, cross-tenant leakage, what happens when the dependency you mocked behaves differently in production.
- Coverage numbers are treated as a *floor*, not a ceiling. 95% coverage that misses the one path that matters is worse than 70% that doesn't.
- The synthesis step is still done. "All tests pass" is the start of the conversation, not the end.

## Common failure modes

- **Treating the agent's output as the answer.** It's the draft. Synthesis is the answer.
- **Confusing coverage with confidence.** Coverage measures what was executed, not what was reasoned about.
- **Letting the agent decide what's worth testing.** Agents optimise for plausible cases. Humans should decide which *implausible* ones still matter.
- **Skipping the "why is this safe to delegate" check.** Some technical tickets are technical on the surface and strategic underneath (see [Case 3](examples/case-studies.md#case-3--strategic-layer-overrides-everything-else)).

## Questions to ask in refinement

- What are the failure modes the spec does *not* describe?
- What does this system do when its dependencies misbehave?
- What would the agent miss because the agent has never read an incident report?
- Is there anything in this ticket that looks technical but is actually a strategic decision in disguise?

## See it applied

- [Case 1 — Refactor of the checkout retry logic](examples/case-studies.md#case-1--technical-layer-wins) — aggressive delegation, with the synthesis step catching a clock-skew bug and a PII log line the agent had no way to weigh.
