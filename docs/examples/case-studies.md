# Case Studies

> Worked examples of Judgement-First Testing applied to real-shaped tickets.
> Names, products, and numbers are fictional. The decisions are not.

Each case follows the same shape:

1. **The ticket** — what landed in the backlog.
2. **The three-sentence risk pass** — technical, human, strategic.
3. **What was delegated, what wasn't.**
4. **What the agent produced.**
5. **What the human added — and why it mattered.**
6. **Outcome.**

---

## Case 1 — Technical Layer Wins
### *Refactor of the checkout retry logic*

**The ticket**
> "Refactor `PaymentRetryService` to use exponential backoff. Existing unit tests must pass. Add coverage for the new backoff curve."

A bounded, well-specified change to a service with a clean interface and an existing test suite.

**Three-sentence risk pass**
- *Technical:* Backoff curve could overshoot the gateway's rate limit; jitter must be correct; idempotency keys must survive retries.
- *Human:* None directly — no UI change, no user-facing copy.
- *Strategic:* Low. The change is reversible behind a feature flag.

**Delegation decision**
Almost everything goes to the agent. This is the layer the framework says to delegate aggressively, and the ticket fits the shape: clear spec, deterministic behaviour, existing tests as a safety net.

**What the agent produced**
- A parameterised test suite covering 0, 1, 2, 3, and max-retry scenarios.
- Property-based tests for the backoff curve (monotonic, bounded, jittered within tolerance).
- A load test simulating gateway 429 responses at 50/100/500 RPS.
- Mutation testing report: 94% killed mutants.

**What the human added**
- Noticed the agent had not tested the **clock-skew case** — what happens when the retry timer fires during a system time jump (NTP correction, container migration). Added one test. It failed.
- Vetoed the agent's suggestion to log the full request payload on retry — PII risk the agent had no context to weigh.

**Outcome**
Shipped in two days instead of five. The clock-skew bug would have surfaced in production within a month based on historical incident frequency. The PII log line would have triggered a compliance review.

**Lesson**
*Delegate aggressively, but the synthesis step is not optional even when the layer is "safe".*

---

## Case 2 — Human Layer Catches What Coverage Cannot
### *New onboarding flow for first-time users*

**The ticket**
> "Implement the 3-step onboarding wizard per Figma. All form validation per spec. Acceptance criteria attached."

Every acceptance criterion was testable. Every field had a validation rule. The agent could automate all of it.

**Three-sentence risk pass**
- *Technical:* Standard form handling. Low risk.
- *Human:* High. This is the first interaction a new user has with the product. Friction here costs activation, not just NPS.
- *Strategic:* Medium-high. Onboarding completion rate is a tracked north-star metric for the quarter.

**Delegation decision**
The agent owns the technical layer: field validation, accessibility checks, cross-browser regression, API contract tests. A human owns the human layer — and explicitly *blocks the ticket from closing* until exploratory testing is done with at least three real users from outside the team.

**What the agent produced**
- 47 automated tests. All passing.
- Accessibility audit: WCAG 2.2 AA compliant.
- Cross-browser pass on Chrome, Safari, Firefox, Edge.

By every machine-measurable standard, the feature was ready.

**What the human added**
Sat next to three colleagues who had never seen the product. Watched.
- All three hesitated on step 2. The "Continue" button was below the fold on a 13" laptop. None scrolled. Two tried to click the logo.
- The error message *"Invalid input"* on the company-size field was technically correct and emotionally useless. One user re-entered the same value three times before giving up.
- The "Skip for now" link was the same colour as the body text. Two users didn't see it existed.

None of this was in the spec. None of it would have been caught by any automated test. All of it was the actual product.

**Outcome**
Three changes shipped before release: sticky CTA, specific error copy, restyled secondary action. Onboarding completion rose 11 points in the first week post-launch.

**Lesson**
*A passing test suite tells you the code does what was written. It does not tell you the feature works.*

---

## Case 3 — Strategic Layer Overrides Everything Else
### *AI-generated product recommendations on the homepage*

**The ticket**
> "Integrate the new recommendation model into the homepage carousel. A/B test at 10% traffic. Ship by end of sprint."

A standard A/B test ticket. Backend ready. Frontend ready. Test plan ready in fifteen minutes once the agent had the API contract.

**Three-sentence risk pass**
- *Technical:* Caching, fallback when model times out, telemetry. Tractable.
- *Human:* Recommendations could feel uncanny or off-brand. Worth a review.
- *Strategic:* **The model was trained on a dataset that included a partner brand's product taxonomy under an expiring licence.** No one on the QA side had been told. The legal expiry was 38 days away.

That third sentence didn't come from a tool. It came from a fifteen-minute conversation in refinement where the QA lead asked, *"Where does the training data come from, and what happens when it stops being ours?"*

**Delegation decision**
The technical and human layers proceed as normal — agent does the test plan, automation, telemetry checks; human does exploratory review of recommendation quality.

But the *go/no-go decision* is escalated. The agent has no way to weigh a 38-day licence cliff against a sprint deadline. That is exactly the kind of context the Strategic layer exists to hold.

**What the agent produced**
- Full functional test pass.
- Load test green at 10x expected traffic.
- Fallback behaviour verified.
- Telemetry dashboards live.

By every operational measure, the feature was shippable.

**What the human added**
A one-page risk note that went to the product lead and engineering director before the A/B test was enabled. It contained three options:
1. Ship at 10% as planned, accept rebuild work in 38 days.
2. Delay one sprint, retrain on owned data, ship clean.
3. Ship behind a kill switch with a calendar-bound auto-disable.

Option 3 was chosen. The kill switch fired on day 37. No incident. No legal exposure. No scramble.

**Outcome**
The feature shipped on time. It also shipped *survivably*. The agent's output was correct and complete. It was also, on its own, not the answer.

**Lesson**
*The agent answers the question you asked. Strategic judgement is the practice of asking the question no one wrote down.*

---

## Patterns Across the Three Cases

| | Case 1 | Case 2 | Case 3 |
|---|---|---|---|
| Layer the agent dominated | Technical | Technical | Technical |
| Layer that caught the real risk | Technical (synthesis step) | Human | Strategic |
| Would automated metrics have flagged it? | No | No | No |
| Time cost of the human step | ~30 min | ~2 hours | ~15 min in refinement |
| Cost if skipped | 1 production incident | 11pt drop in activation | Legal & rebuild exposure |

The pattern is consistent: the agent's output was never wrong. It was incomplete in a way that only judgement can complete.

That is the whole framework, in three tickets.

---

## Using These as a Template

For your next ticket, before opening an agent:

1. Write the three-sentence risk pass.
2. Decide, on paper, which layer owns this ticket's hardest problem.
3. Decide what the agent *cannot* answer, and who will answer it instead.
4. Run the agent.
5. Do the synthesis step. Out loud, if it helps.

If steps 1–3 take longer than the agent takes to produce its output, that is not a problem with the framework. That is the framework working.

---

[← Back to README](../../README.md)
