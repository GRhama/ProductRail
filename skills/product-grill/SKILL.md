# Skill: product-grill

## Purpose

Find the smallest set of human decisions required to make expected Product behavior sufficiently deterministic for Engineering.

## Input

A natural-language product request plus optional context.

## Method

1. Restate the problem in plain language.
2. List what is already decided.
3. Detect missing behavioral decisions using internal lenses:
   trigger, time, state, eligibility, result, downstream, correction, exception, failure, auditability.
4. Prioritize blockers only.
5. Ask atomic questions in business language.
6. Prefer no more than ~6 blocking decisions in the first round.
7. Accept long free-form answers.
8. Treat stakeholder speech as evidence, not as final specification text.
9. Extract:
   - evidence;
   - proposed interpretations;
   - rationale;
   - contradictions;
   - unresolved gaps.
10. Ask a human to confirm each proposed interpretation.
11. Mark only human-confirmed interpretations `RESOLVED`.
12. Re-grill only unresolved delta.
13. Update persistent state after each relevant transition.

## Output

For each decision:

```text
DEC-XXX — Title

Question:
...

Why this must be decided:
...

Evidence:
...

Proposed interpretation:
...

Human confirmation:
PENDING | CONFIRMED

Status: OPEN | RESOLVED
```

When no Product Grill blocker remains, pass confirmed decisions to `feature-spec`. Do not declare `PRODUCT_READY` from this skill.

## Anti-patterns

- fixed questionnaire;
- dozens of low-value questions;
- architecture questions disguised as product questions;
- inventing missing behavior;
- resolving an inferred interpretation without human confirmation;
- repeating already resolved questions.
