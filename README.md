# ProductRail

Turn ambiguous product requests into explicit decisions, specifications and engineering-ready work.

ProductRail is a domain-agnostic workflow for AI-assisted Product Management built around explicit decisions, contracts, gates, handoffs and persisted state.

> AI helps structure the work.
>
> Humans keep decision authority.

[![Version](https://img.shields.io/badge/version-v0.1-blue)](#status)
[![Status](https://img.shields.io/badge/status-experimental-orange)](#status)
[![Model agnostic](https://img.shields.io/badge/model-agnostic-6f42c1)](#model-agnostic)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

## Why ProductRail

A stakeholder says:

> “We need users to schedule reports and receive them by email.”

Without structured discovery, an AI may silently assume:

- who can schedule;
- recurrence;
- timezone;
- failure behavior;
- edit/cancel rules;
- technical implementation.

ProductRail forces those assumptions to become explicit decisions before Engineering starts.

## Before / after

**Without ProductRail**

```text
request → AI-generated requirements → hidden assumptions → engineering clarification
```

**With ProductRail**

```text
request → Product Grill → confirmed decisions → Feature Spec → stories → Engineering validation
```

## How it works

```text
REQUEST
→ PRODUCT GRILL
→ HUMAN CONFIRMATION
→ FEATURE SPEC
→ PRODUCT_READY
→ STORIES + ACCEPTANCE CRITERIA
→ STORIES_READY
→ ENGINEERING GRILL
→ ENGINEERING_READY
→ IMPLEMENTATION SPEC
→ SPEC-TO-TASKS
→ TASKS_READY
→ IMPLEMENTATION
→ TESTS
→ VERIFICATION
```

This is a concise view. [`docs/workflow.md`](docs/workflow.md) defines the normative state machine and every gate contract.

## Try it in 5 minutes

```bash
git clone https://github.com/GRhama/ProductRail.git
cd ProductRail
```

1. Clone or download the repository.
2. Open [`examples/new-feature/REQUEST.md`](examples/new-feature/REQUEST.md).
3. Replace the sample with your feature request.
4. Give the request and [`skills/product-grill/SKILL.md`](skills/product-grill/SKILL.md) to your AI.
5. Follow the gates in [`docs/workflow.md`](docs/workflow.md).

## PM walkthrough

Use this example throughout the walkthrough:

```text
Feature:
Scheduled report delivery

Initial request:
Users should be able to schedule a report and receive it by email.

Known context:
- reports already exist;
- users can currently generate them manually;
- scheduling does not exist yet.
```

### Step 1 — Create the request

Open [`examples/new-feature/REQUEST.md`](examples/new-feature/REQUEST.md). Replace its sample with the example above or your own feature request.

### Step 2 — Run Product Grill

Give the AI these inputs:

- [`skills/product-grill/SKILL.md`](skills/product-grill/SKILL.md)
- [`examples/new-feature/REQUEST.md`](examples/new-feature/REQUEST.md)
- [`templates/MEETING_PACK.md`](templates/MEETING_PACK.md)
- [`templates/CURRENT_STATE.md`](templates/CURRENT_STATE.md)

Copy this prompt:

```text
Follow the ProductRail Product Grill.

Use:
- skills/product-grill/SKILL.md
- templates/MEETING_PACK.md
- templates/CURRENT_STATE.md

Input:
- examples/new-feature/REQUEST.md

Do not create a solution yet.
Do not make engineering decisions.

Identify only the minimum Product decisions needed
to make the expected behavior deterministic.

Persist the output using the provided templates.
```

Product questions may include:

- who can schedule;
- recurrence;
- timezone;
- failure behavior;
- edit/cancel;
- email delivery failure.

Scheduler, queue and provider choices are Engineering questions. Product Grill must not decide them.

### Step 3 — Stakeholder discussion

Process each answer through this path:

```text
stakeholder speech
→ evidence
→ proposed interpretation
→ human confirmation
→ RESOLVED
```

Stakeholder speech is evidence, not specification. Human confirmation turns a proposed interpretation into a resolved Product decision.

The normative workflow records synthesis between evidence and proposed interpretation.

### Step 4 — Feature Spec

Use [`skills/feature-spec/SKILL.md`](skills/feature-spec/SKILL.md) and [`templates/FEATURE_SPEC.md`](templates/FEATURE_SPEC.md) to persist approved behavior.

### Step 5 — PRODUCT_READY

Do not advance until the persisted gate says:

```text
PRODUCT_READY: YES
```

Use the contract in [`docs/workflow.md`](docs/workflow.md). Do not infer readiness from an incomplete artifact.

### Step 6 — Stories

Use [`templates/STORY_BREAKDOWN.md`](templates/STORY_BREAKDOWN.md).

```text
US-001
As a user,
I want to create a report schedule,
so that reports can be generated automatically.

Acceptance Criteria:

AC-001
Given an eligible user
when a valid schedule is created
then the schedule is persisted and becomes active.

AC-002
Given an active schedule
when its execution time is reached
then one report generation is requested.
```

### Step 7 — STORIES_READY

Do not hand off until the persisted gate says:

```text
STORIES_READY: YES
```

[`templates/STORY_BREAKDOWN.md`](templates/STORY_BREAKDOWN.md) is the authoritative artifact for this gate. A missing, `NO` or unverifiable value blocks the handoff.

### Step 8 — Engineering handoff

Give Engineering the authoritative package:

- approved Feature Spec;
- stories and Acceptance Criteria;
- proof of `STORIES_READY: YES` linked to the authoritative Story Breakdown;
- relevant confirmed decisions;
- deferred and out-of-scope items;
- persisted current state;
- additional references, when they exist.

Engineering validates the handoff before using [`skills/engineering-grill/SKILL.md`](skills/engineering-grill/SKILL.md).

### Step 9 — Engineering flow

```text
ENGINEERING GRILL
→ ENGINEERING_READY
→ IMPLEMENTATION SPEC
→ SPEC-TO-TASKS
→ TASKS_READY
→ IMPLEMENTATION
→ TESTS
→ VERIFICATION
```

See [`docs/workflow.md`](docs/workflow.md) for the complete normative flow, including validation and feedback paths.

## Core gates

These summaries do not replace the gate contracts in [`docs/workflow.md`](docs/workflow.md).

| Gate | Meaning | Authority |
| --- | --- | --- |
| [`PRODUCT_READY`](docs/workflow.md#product_ready) | Product behavior is ready for story definition. | Product |
| [`STORIES_READY`](docs/workflow.md#stories_ready) | Stories are ready for Engineering handoff. | Product |
| [`ENGINEERING_READY`](docs/workflow.md#engineering_ready) | Validated Product work is ready for an Implementation Spec. | Engineering |
| [`TASKS_READY`](docs/workflow.md#tasks_ready) | Implementation tasks are ready for execution. | Engineering |

## Model agnostic

ProductRail is not tied to a specific AI model or vendor.

Core methodology:

- persisted artifacts;
- explicit gates;
- authority boundaries;
- state transitions.

Agents and skills are execution mechanisms.

If a platform does not support native agents or skills, use the repository files as structured prompts or instructions. This approach can be applied with ChatGPT, Claude, GitHub Copilot, Codex and other LLM tools without claiming native integration.

## Repository structure

```text
agents/      Agent role definitions
skills/      Repeatable workflow procedures
templates/   Persistent artifact formats
docs/        Normative workflow and supporting guidance
examples/    Generic starting requests
```

- [`agents/`](agents/) defines Product, Engineering and reviewer roles.
- [`skills/`](skills/) contains Product and Engineering procedures.
- [`templates/`](templates/) provides formats for durable workflow artifacts.
- [`docs/`](docs/) contains the normative workflow and supporting documentation.
- [`examples/`](examples/) provides new product, new feature and improvement starting points.

## Status

ProductRail v0.1 is an experimental, public workflow.

It has been:

- internally tested;
- adversarially reviewed;
- checked for gate consistency;
- checked for public/domain leakage.

ProductRail v0.1 does not claim production readiness or performance results.

Released under the [MIT License](LICENSE).
