# Skill: engineering-grill

## Purpose

Confront an approved Product contract with the current repository before implementation.

## Source priority

1. executable code and tests;
2. current repository configuration;
3. current technical documentation;
4. historical documentation.

## Preconditions

- validate the minimum Product-to-Engineering handoff package defined in `docs/workflow.md`;
- verify `STORIES_READY: YES` against the referenced authoritative Story Breakdown artifact;
- if `STORIES_READY` is absent, `NO` or not verifiable, mark the handoff `INVALID`, do not start Engineering Grill, and return the flow to Product;
- stop and return an incomplete or inconsistent package to Product;
- record validation in persistent state.

## Method

1. Map relevant modules, entry points and tests.
2. Describe current behavior with concrete evidence.
3. Compare current behavior against the Feature Spec.
4. Identify gaps, contradictions and hidden assumptions.
5. Classify every unresolved issue using `decision-classifier`.
6. Return only true Product gaps to Product.
7. Record technical consequences for Engineering.
8. Define the smallest scope that satisfies the story.
9. Update persistent state with classifications, blockers, evidence and next action.

## Output

```text
CURRENT_BEHAVIOR
...

GAPS
- ...

PRODUCT_QUESTIONS
- ...

TECHNICAL_CONSEQUENCES
- ...

ENGINEERING_READY: YES | NO
```

Set `ENGINEERING_READY: YES` only when the full gate contract in `docs/workflow.md` is satisfied.

## Rules

- Do not implement during the grill.
- Do not refactor unrelated code.
- Do not reinterpret Product intent to fit the current architecture.
- Do not treat missing infrastructure as Product ambiguity unless behavior depends on it.
