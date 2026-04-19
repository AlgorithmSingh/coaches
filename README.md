# coaches

Reusable coach prompts for triaging information and reviewing agent output. Each file is a self-contained prompt — paste into a fresh Claude (or any capable LLM) chat.

Source conversation: [`../daily/2026-04-18/learning-and-review-coach-prompts.md`](../daily/2026-04-18/learning-and-review-coach-prompts.md).

## The two families

**Drilling coaches** put me in the hot seat — I answer, the coach probes. Use to build real understanding.

| File | Use when |
|---|---|
| [`learning-coach.md`](./learning-coach.md) | Drowning in information. Runs triage → Feynman → Socratic in one session. |
| [`triage-coach.md`](./triage-coach.md) | Just need to cut noise fast. Compression + delta only. |
| [`feynman-coach.md`](./feynman-coach.md) | Want to find holes in my own understanding. I explain, it finds gaps. |
| [`socratic-coach.md`](./socratic-coach.md) | Want to understand one concept deeply. It drills via questions. |

**Review coaches** are for reviewing agent output before green-lighting it.

| File | Use when |
|---|---|
| [`tradeoff-review-coach.md`](./tradeoff-review-coach.md) | Agent wrote a plan. Review the decisions *before* the steps. |
| [`plan-review-coach.md`](./plan-review-coach.md) | Agent wrote a plan. Drill the steps themselves. |
| [`plan-qa-explainer.md`](./plan-qa-explainer.md) | Want a *reviewable Q&A artifact* of the plan, not a drilling session. |
| [`code-explainer.md`](./code-explainer.md) | Agent wrote dense code. Walk it in four phases: orient → mechanics → decisions → risks. |

## When to reach for which coach

Match the situation to the coach, not the other way around.

**"The agent dumped a pile of output on me and I don't know where to start."**
→ [`triage-coach.md`](./triage-coach.md). Compress each chunk to one sentence, state the delta. Cut anything with no delta and no decision impact. Fastest of the set.

**"I'm drowning in info and want to actually understand what survives."**
→ [`learning-coach.md`](./learning-coach.md). Runs triage → Feynman → Socratic in one session. Use when I'll do all three anyway; splitting would force re-pasting context.

**"I think I understand something — want to check before I rely on it."**
→ [`feynman-coach.md`](./feynman-coach.md). I explain to an imaginary colleague; it flags where I hedged, used undefined jargon, or skipped steps. Detection only, no teaching.

**"There's one concept I want to really understand."**
→ [`socratic-coach.md`](./socratic-coach.md). It drills via questions, refuses to accept hedged answers. Slowest. Worth it for the 1–2 concepts that matter, not a dozen.

**"My coding agent wrote a plan. Is it even optimizing for the right things?"**
→ [`tradeoff-review-coach.md`](./tradeoff-review-coach.md). Reconstruct the decision tree, surface rejected alternatives, check alignment with my priorities. **Run this before reviewing the steps** — if the agent optimized wrong, reviewing steps is polishing a plan that shouldn't exist.

**"My coding agent wrote a plan. Do the individual steps hold up?"**
→ [`plan-review-coach.md`](./plan-review-coach.md). For each step: what does it do, what breaks without it, what does it assume? Run *after* tradeoff review.

**"I want a reviewable Q&A document of the plan, not a drilling session."**
→ [`plan-qa-explainer.md`](./plan-qa-explainer.md). Produces an artifact I read and mark up. Good for dense plans where I want something annotatable. Worse for internalizing — the drilling coaches are better for that.

**"Agent wrote dense code. I can't hold it in my head."**
→ [`code-explainer.md`](./code-explainer.md). Four phases: orient → mechanics → decisions → risks. Tell it upfront whether I need to *approve*, *maintain*, or *modify* — it calibrates depth.

**"I only have 5 minutes."**
→ `triage-coach` or skim the output of `plan-qa-explainer`. Skip every drilling coach; they need time.

**"I have an hour and this really matters."**
→ Full pipeline (see below), or `learning-coach` for pure info overload.

## Full pipeline for expensive changes

```
tradeoff-review → plan-qa-explainer → [agent executes] → code-explainer
```

Each stage catches a different class of problem. Don't run all four every time — save the full pipeline for changes where being wrong is expensive. For routine work, just `code-explainer`.

For raw info overload (not agent output), use the drilling coaches.

## Drilling vs. production

The drilling coaches withhold answers by design — that's what makes them work. The Q&A explainer flips it: it produces a document I read and react to. Use drilling to internalize, use the Q&A artifact when I want something to mark up.

Nice chain: run `plan-qa-explainer` first → skim → flag 3–5 questions that bother me → feed just those into `socratic-coach` for depth.
