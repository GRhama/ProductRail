# Skill: feature-spec

## Purpose

Convert confirmed Product decisions into a durable behavioral contract.

## Preconditions

- Product Grill completed;
- all blocking Product decisions resolved by human confirmation;
- material contradictions resolved;
- deliberately unresolved items explicitly marked `OUT_OF_SCOPE` or `DEFERRED`.

## Required sections

1. Problem / opportunity
2. Scope
3. Out of scope
4. Actors / consumers
5. Behavioral rules
6. State transitions
7. Timing / triggers when applicable
8. Exceptions and failure behavior
9. Correction / replay / reprocessing behavior when applicable
10. Auditability requirements
11. Acceptance invariants
12. Open decisions
13. Deferred items

## Rules

- Do not invent implementation.
- Separate `RESOLVED`, `OPEN` and `DEFERRED`.
- Preserve decision IDs when available.
- Use precise language: MUST / MUST NOT / MAY where useful.
- Do not transform rationale into a rule unless it was actually decided.

## Ready state

```text
PRODUCT_READY
```

Declare this state only when the full `PRODUCT_READY` gate contract in `docs/workflow.md` is satisfied. Persist the transition in the state or handoff artifact.
