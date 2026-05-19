# Human Layer

*What the user actually experiences.*

Focuses on the people who use and operate the system. Agents can map this layer but cannot feel it.

## Areas
- Usability testing
- Accessibility (WCAG)
- User acceptance testing
- Operational readiness
- Cognitive load and emotional response

## Delegation
**Requires a human in the loop.** AI can surface candidate flows, generate personas, or summarise feedback — but interpretation, empathy, and exploratory judgement stay with the tester.

---

## What good looks like

- The agent maps the flow, generates personas, runs accessibility audits, and pre-screens copy.
- A human watches **real people use the thing**, ideally people from outside the team, ideally on their own device.
- Exploratory sessions are treated as first-class work, not as something that happens "if there's time".
- Findings are written in the user's language, not the system's: *"Two users hesitated and tried to click the logo"*, not *"CTA discoverability score below threshold"*.

## Common failure modes

- **Shipping because the test suite is green.** A passing suite tells you the code does what was written. It does not tell you the feature works.
- **Replacing exploratory testing with synthetic personas.** An agent persona never gets frustrated, never abandons, never re-reads an error message three times before giving up.
- **Trusting accessibility tooling alone.** WCAG-AA pass ≠ usable for the people the standard exists to protect. Tooling catches the floor, not the experience.
- **Closing the ticket without anyone outside the team having touched the build.**

## Questions to ask in refinement

- Who is the real first-time user for this, and have we watched one?
- Where in this flow could a reasonable person get confused, frustrated, or excluded?
- What does this feature *feel* like when it goes wrong?
- If the only evidence of quality is automated, what are we not seeing?

## See it applied

- [Case 2 — New onboarding flow for first-time users](examples/case-studies.md#case-2--human-layer-catches-what-coverage-cannot) — 47 passing tests, WCAG-AA clean, and still three problems that only surfaced when real users sat down with the build.
