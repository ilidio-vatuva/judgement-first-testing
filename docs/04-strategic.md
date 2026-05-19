# Strategic Layer

*What the business cannot afford to get wrong.*

Ensures testing effort aligns with business outcomes and accepted risk.

## Areas
- Risk-based prioritisation
- Value stream alignment
- Compliance and governance
- Long-term maintainability and roadmap impact

## Delegation
**Not delegable.** No agent owns the consequence of getting this wrong. Strategic judgement — what to test, what to ignore, what to escalate — stays with humans accountable to the business.

---

## What good looks like

- Risk is named *before* a test is written, in plain language, by someone accountable for the outcome.
- The team can articulate, for any given feature, what would actually happen if it failed in production — to users, to revenue, to compliance, to trust.
- Go/no-go decisions are made by humans with context the agent does not have: roadmap, partnerships, contracts, incident history, organisational risk appetite.
- Strategic risk is documented in a form a director can act on (one page, three options, recommended path), not buried in a test report.

## Common failure modes

- **Confusing "all tests pass" with "safe to ship".** Operational readiness is not the same as strategic readiness.
- **Asking the agent to weigh trade-offs.** Agents answer the question they were asked. They do not know which question you should have asked.
- **Treating refinement as a formality.** Most strategic risk is caught (or missed) in the conversation *before* the ticket is groomed.
- **No escalation path.** If the QA function has no route to flag strategic risk to people who can act on it, the layer effectively doesn't exist.

## Questions to ask in refinement

- What would this feature *failing in production* actually cost?
- What dependencies — data, partners, contracts, licences — does this rely on, and when do they expire or change?
- What does this ticket assume about the world that may not be true in six weeks?
- Who needs to know about this risk, and how will they hear about it?

## See it applied

- [Case 3 — AI-generated product recommendations on the homepage](examples/case-studies.md#case-3--strategic-layer-overrides-everything-else) — every operational measure said ship; a single refinement question exposed a 38-day licence cliff and changed the rollout plan.
