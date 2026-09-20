# AI Product Workflow

A reusable, domain-agnostic workflow for turning ambiguous product problems into implementation-ready specifications with AI-assisted agents and skills.

## Core idea

This is not a collection of prompts. It is a protocol of **states, contracts and authority**.

```text
PROBLEM
  ↓
PRODUCT GRILL
  ↓
MEETING PACK
  ↓
STAKEHOLDER DISCUSSION
  ↓
HUMAN CONFIRMATION + DELTA REGRILL
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
ENGINEERING GRILL
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
IMPLEMENTATION
  ↓
TESTS
  ↓
REVIEW
```

## Authority model

- Product decides expected behavior.
- AI finds ambiguity and structures decisions.
- Product contracts persist approved behavior.
- Engineering validates specifications against the real repository.
- AI can help decompose work into small tasks.
- Developers validate implementation and commit.

## What problem does it solve?

AI can generate requirements quickly, but speed does not remove ambiguity.

This workflow tries to reduce:

- implicit product decisions made during implementation;
- repeated clarification meetings;
- specification drift;
- context loss between Product and Engineering;
- large, vague implementation tasks;
- unnecessary re-reading of the repository.

## Supported use cases

The workflow is intended for:

- new products;
- new features in existing products;
- improvements to systems already in production.

It is intentionally domain-agnostic.

## v0.1 contents

### Agents

- `product.agent.md`
- `engineering.agent.md`
- `reviewer.agent.md`

### Core skills

- `product-grill`
- `decision-classifier`
- `feature-spec`
- `engineering-grill`
- `implementation-spec`
- `spec-to-tasks`
- `spec-verification`

### Templates

- `PRODUCT_CONTEXT.md`
- `MEETING_PACK.md`
- `FEATURE_SPEC.md`
- `ENGINEERING_GRILL.md`
- `IMPLEMENTATION_SPEC.md`
- `STORY_BREAKDOWN.md`
- `CURRENT_STATE.md`

## State model

```text
DISCOVERY
  ↓
PRODUCT_READY
  ↓
STORIES_READY
  ↓
ENGINEERING_READY
  ↓
TASKS_READY
  ↓
DONE / PASS
```

A state should only advance when its contract is satisfied.

[`docs/workflow.md`](docs/workflow.md) is the normative state machine and defines every gate contract. This README is a summary.

Every relevant state transition must update a persistent state or handoff artifact. A new session must be able to continue without conversation memory.

## Important rule

Do not make technical implementation decisions during Product discovery unless the technical constraint is itself a product constraint.

Likewise, Engineering should not silently invent missing product behavior. When a real behavior gap is found, classify it and return only the minimum decision necessary to Product.

## Example

See `examples/` for three generic starting points:

- new product;
- new feature;
- improvement to an existing product.

## Tools

The workflow can be adapted to different AI tools. The original experiments used combinations of conversational AI for Product and coding agents in repository-aware environments for Engineering.

The method is more important than the vendor.

## Status

`v0.1` — public portfolio version. Intentionally small.
