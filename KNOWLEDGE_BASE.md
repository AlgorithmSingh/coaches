# KNOWLEDGE_BASE.md

Snapshot of the current state of the reusable coach-prompt library. Paired with `README.md` and `AGENTS.md`.

**Last verified:** 2026-04-19 (coach library consists of drilling prompts, review prompts, and a source link back to `daily-journal/2026-04-18/learning-and-review-coach-prompts.md`)

---

## 1. Project identity

- **Name:** coaches.
- **Purpose:** reusable prompts for learning from dense material and reviewing coding-agent output before approval.
- **Nature:** prompt library, not a software runtime.

## 2. Source and current scope

The current library is grounded in:

- `README.md` — explains the families and how to choose between them
- `../../daily-journal/2026-04-18/learning-and-review-coach-prompts.md` — source conversation / provenance link

The files are designed to be pasted into a fresh capable LLM chat as self-contained prompts.

## 3. Two coach families

### 3.1 Drilling coaches

These put the human in the hot seat and probe understanding.

| File | Use when |
|---|---|
| `learning-coach.md` | Need one session that runs triage -> Feynman -> Socratic. |
| `triage-coach.md` | Need fast compression and delta-only signal extraction. |
| `feynman-coach.md` | Want to expose holes in your explanation. |
| `socratic-coach.md` | Want to understand one concept deeply through questions. |
| `watch-coach.md` | Want the same learning flow but framed for video transcripts. |

### 3.2 Review coaches

These are for reviewing agent output before green-lighting it.

| File | Use when |
|---|---|
| `tradeoff-review-coach.md` | Review the decisions behind a plan before reviewing the steps. |
| `plan-review-coach.md` | Drill the plan steps themselves. |
| `plan-qa-explainer.md` | Produce a reviewable Q&A artifact of a plan. |
| `code-explainer.md` | Walk dense code via orient -> mechanics -> decisions -> risks. |

## 4. Recommended usage patterns

Current documented chains from `README.md`:

- **Expensive change review:** `tradeoff-review -> plan-qa-explainer -> [agent executes] -> code-explainer`
- **Pure info overload:** use the drilling coaches instead of the review chain
- **Video transcript learning:** use `watch-coach.md`, or the watch-agent-specific coaches when working inside `watch-agent-system/coach/`

Important distinction:

- **Drilling coaches** withhold answers on purpose to force understanding.
- **Q&A explainers** produce an artifact to read and mark up.

## 5. Current artifact map

| Path | Role |
|---|---|
| `README.md` | Main map of the coach library. |
| `AGENTS.md` | Scoped instructions for maintaining and using this folder. |
| `KNOWLEDGE_BASE.md` | This state snapshot. |
| `triage-coach.md` | Fast compression / delta extraction. |
| `learning-coach.md` | Combined learning flow. |
| `feynman-coach.md` | Gap-finding explanation check. |
| `socratic-coach.md` | Question-driven deep understanding. |
| `tradeoff-review-coach.md` | Decision-level plan review. |
| `plan-review-coach.md` | Step-level plan review. |
| `plan-qa-explainer.md` | Q&A plan artifact generator. |
| `code-explainer.md` | Code walkthrough prompt. |
| `watch-coach.md` | Transcript/video-learning variant. |

## 6. Current maturity

- **Implemented:** prompt library and usage guidance.
- **Not implemented:** no automation, no CLI, no scoring harness, no prompt-selection router.
- **Truthful description:** this is a curated set of reusable prompts and a README that explains when to use which one.

## 7. What to preserve when extending this folder

- Every coach should have a clear use case.
- Families should stay distinct: learning / drilling vs review / approval.
- The README should remain the entrypoint for coach selection.
- Provenance back to the daily-journal source note should be preserved.

