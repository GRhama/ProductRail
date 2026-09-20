# Skill: implementation-spec

## Purpose

Turn one approved story into an implementation-ready technical plan after Engineering Grill.

## Preconditions

- Feature Spec is approved;
- story and acceptance criteria are known;
- Engineering Grill is complete;
- `ENGINEERING_READY: YES` under the gate contract in `docs/workflow.md`.

## Required sections

1. Story / goal
2. Existing behavior
3. Scope
4. Out of scope
5. Files / modules likely affected
6. Technical design
7. Data / state transitions
8. Error and retry behavior
9. Idempotency / replay considerations when relevant
10. Test strategy
11. Acceptance criteria mapping
12. Risks / deviations

## Rules

- Prefer minimum change.
- Reuse existing abstractions when they satisfy the contract.
- Do not solve future stories.
- Do not introduce infrastructure not required by the story.
- Make unknowns explicit.

## Output state

The completed Implementation Spec is input to `spec-to-tasks`. It does not declare `TASKS_READY`.

Persist completion and next action in the state or handoff artifact.
