# Workflow

This document defines the normative state machine. Other flow diagrams are summaries and must remain consistent with it.

## Normative state machine

```text
REQUEST
  ↓
PRODUCT GRILL
  ↓
MEETING PACK
  ↓
STAKEHOLDER DISCUSSION
  ↓
EVIDENCE + SYNTHESIS + PROPOSED INTERPRETATION
  ↓
HUMAN CONFIRMATION
  ↓
DELTA REGRILL (when needed)
  ↓
FEATURE SPEC
  ↓
PRODUCT_READY
  ↓
STORIES + ACCEPTANCE CRITERIA
  ↓
STORIES_READY
  ↓
PRODUCT → ENGINEERING HANDOFF VALIDATION
  ↓
ENGINEERING GRILL + GAP CLASSIFICATION
  ↓
PRODUCT QUESTION + CONTRACT UPDATE (when needed; then revalidate and re-grill the affected delta)
  ↓
ENGINEERING_READY
  ↓
IMPLEMENTATION SPEC
  ↓
SPEC-TO-TASKS
  ↓
SMALL, VERIFIABLE TASKS
  ↓
TASKS_READY
  ↓
IMPLEMENT
  ↓
TEST
  ↓
VERIFY
  ↓
DONE / PASS
```

## Gate contracts

### PRODUCT_READY

`PRODUCT_READY: YES` only when:

- no blocking Product decisions remain open;
- no material contradictions remain unresolved;
- behavior required by Engineering is defined;
- deliberately unresolved items are explicitly `OUT_OF_SCOPE` or `DEFERRED`;
- no AI inference has been promoted to a decision without human confirmation.

Stakeholder speech is evidence, not a decision by itself. Use this decision path:

```text
stakeholder speech
  ↓
evidence
  ↓
synthesis
  ↓
proposed interpretation
  ↓
human confirmation
  ↓
RESOLVED
```

AI may extract multiple proposed decisions from a long answer. It must not mark an inferred interpretation `RESOLVED` without human confirmation.

### STORIES_READY

`STORIES_READY: YES` only when:

- each story has a clear objective;
- scope is bounded;
- acceptance criteria are observable and testable;
- relevant dependencies are identified;
- no blocking Product decision is hidden in a story;
- every story remains consistent with the Feature Spec.

### ENGINEERING_READY

`ENGINEERING_READY: YES` only when:

- the Feature Spec has been confronted with the repository;
- all discovered gaps are classified;
- all `PRODUCT_DECISION` blockers are resolved;
- required `PRODUCT_CONFIRMATION` is complete;
- each `TECHNICAL_CONSEQUENCE` remains under Engineering authority;
- each `ALREADY_DECIDED` points to an existing contract;
- technical scope is bounded;
- no known blocker prevents creation of the Implementation Spec.

### TASKS_READY

`TASKS_READY: YES` only after:

- the Implementation Spec is complete;
- `spec-to-tasks` has decomposed it;
- each resulting task is small and independently verifiable;
- task scope, dependencies, validation and completion criteria are explicit;
- no task contains an unresolved blocker.

An Implementation Spec cannot declare `TASKS_READY`.

## Product to Engineering handoff

The minimum authoritative package contains:

- approved Feature Spec;
- stories and acceptance criteria;
- proof of `STORIES_READY: YES`, with a reference to the authoritative Story Breakdown artifact that declared it;
- relevant confirmed decisions;
- deferred and out-of-scope items;
- persistent context required to continue the work;
- additional references, when they exist.

Engineering validates package presence, approval status, internal consistency and readable references before Engineering Grill. If `STORIES_READY` is absent, `NO` or not verifiable against its referenced artifact, the handoff is `INVALID`, Engineering Grill must not run, and the flow returns to Product.

## Context persistence

Context persistence is a protocol obligation. Every relevant transition, including readiness gates, Product questions and contract updates, must update a persistent state or handoff artifact. The artifact must let a new session continue without conversation memory.

At minimum, persist current state, authoritative artifacts, confirmed and open decisions, deferred and out-of-scope items, completed work, blockers, evidence or validation, and next action. `templates/CURRENT_STATE.md` provides a vendor-neutral format.

## Key idea

A Product gap discovered by Engineering should be patched into the Product contract, not silently decided in code.

A technical consequence of an already-approved behavior should remain with Engineering, not be escalated to stakeholders.
