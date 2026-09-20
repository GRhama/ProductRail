# Skill: spec-to-tasks

## Purpose

Decompose an Implementation Spec into small, independently reviewable tasks.

## Task quality rules

Each task should:

- have one primary objective;
- have bounded file/module scope when possible;
- include observable completion criteria;
- identify tests to run or add when allowed;
- avoid unrelated refactors;
- preserve dependencies explicitly.

## Format

```text
TASK-XXX — Title

OBJECTIVE
...

SCOPE
...

OUT_OF_SCOPE
...

CHANGES
...

VALIDATION
...

DEPENDENCIES
...

DONE_WHEN
...
```

## Rule

If a task cannot be described without multiple independent objectives, split it.

Do not declare readiness until every task is small and independently verifiable, with explicit scope, dependencies, validation and completion criteria. No task may contain an unresolved blocker.

## Ready state

After decomposition satisfies the full gate contract in `docs/workflow.md`:

```text
TASKS_READY: YES
```

Persist the task set, readiness result and next action in the state or handoff artifact.
