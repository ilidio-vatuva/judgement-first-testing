# Contributing

Thanks for considering a contribution. This repo is a small, opinionated framework, not a sprawling platform — contributions are welcome but lightly scoped.

## What this repo wants

- **Anonymised case studies** from real tickets where the framework helped (or failed).
- **Sharpenings** of existing wording: shorter, clearer, more honest.
- **Corrections**: broken links, factual errors, dead references.
- **Translations** of the README or layer docs.

## What this repo doesn't want

- New layers, new ceremonies, new mandatory artefacts. The framework is deliberately a decision layer, not a process.
- Tool recommendations or vendor comparisons.
- Generic "AI in QA" essays. There are plenty elsewhere.

---

## Submitting a case study

Case studies are the most valuable contribution. They turn the framework from theory into pattern.

### Use the existing shape

Match the structure in [docs/examples/case-studies.md](docs/examples/case-studies.md):

1. **The ticket** — one or two lines, in the form it arrived.
2. **Three-sentence risk pass** — technical, human, strategic.
3. **Delegation decision** — what went to the agent, what didn't, why.
4. **What the agent produced** — bullet list, factual.
5. **What the human added** — the specific thing that wouldn't have surfaced otherwise.
6. **Outcome** — what shipped, what changed, what it cost or saved.
7. **Lesson** — one sentence.

If it doesn't fit that shape, it's probably a blog post, not a case study.

### Anonymisation checklist

Before opening a PR, confirm:

- [ ] No real product, company, team, or person names.
- [ ] No internal system names, repo paths, or ticket IDs.
- [ ] No verbatim copy from internal docs, Slack, or tickets.
- [ ] Numbers are either rounded, ranged, or replaced with order-of-magnitude figures.
- [ ] Anyone from the original team would read it and not be able to point to a specific incident.
- [ ] You have the right to share the underlying pattern (check your employment / NDA terms if unsure).

If in doubt, **make it more abstract**. The pattern is the value. The specifics are the risk.

### Length

Aim for the length of the existing three cases (~250–400 words each). If it's longer, it's probably carrying details that should be cut.

---

## Submitting any other change

1. Open an issue first for anything non-trivial (more than a typo or a broken link). A two-line description of the change you're proposing is enough.
2. Keep PRs small. One change per PR.
3. Match the tone of the existing docs: direct, lower-case where the originals are, no hedging, no marketing voice.
4. No emoji unless the existing file already uses them (it doesn't).

## What gets merged

PRs are reviewed against three questions:

- Does it make the framework **easier to apply**, or just longer?
- Does it preserve the **delegate execution, keep judgement** rule?
- Would a tired QA engineer on a Friday afternoon actually read it?

If the answer to all three is yes, it goes in.

---

## Conduct

Be straightforward. Disagree with ideas, not people. Assume the other person has read the docs and is acting in good faith. That's the whole policy.
