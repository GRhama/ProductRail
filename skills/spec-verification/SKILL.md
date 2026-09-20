# Skill: spec-verification

## Purpose

Verify that a completed change satisfies the approved Product and Engineering contracts.

## Verify

- Feature Spec rules;
- acceptance criteria;
- Implementation Spec;
- expected state transitions;
- exception/failure behavior;
- tests;
- scope boundaries;
- documentation affected by the change.

## Evidence

Prefer:

- concrete code paths;
- test names;
- executed commands;
- generated outputs;
- observable API/CLI behavior.

## Output

```text
SPEC_VERIFICATION

PASS
- ...

FAIL
- ...

DEVIATIONS
- ...

VERDICT: PASS | PASS_WITH_GAPS | FAIL
```

Do not modify files during verification unless explicitly authorized.

Persist the verdict, evidence, deviations and next action in the state or handoff artifact.
