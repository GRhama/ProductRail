# Engineering Grill

## Inputs

- Feature Spec:
- Story:
- Repository / branch:

## Handoff validation

- [ ] Feature Spec is approved.
- [ ] Stories and acceptance criteria are present.
- [ ] Referenced authoritative Story Breakdown artifact declares `STORIES_READY: YES`.
- [ ] Relevant decisions are present and confirmed.
- [ ] Deferred and out-of-scope items are present.
- [ ] Persistent context is sufficient for a new session.
- [ ] Additional references are readable when provided.

Story Breakdown reference:

Verified gate value: `STORIES_READY: YES | NO | ABSENT | NOT_VERIFIABLE`

Handoff result: `VALID | INVALID`

Only `STORIES_READY: YES` with a verifiable artifact reference permits `VALID`. For any other value, mark `INVALID`, do not execute Engineering Grill, and return the flow to Product.

## Current repository behavior

## Relevant code paths

## Relevant tests

## Contract gaps

## Classified questions

| ID | Question / gap | Class | Evidence | Contract reference | Action |
|---|---|---|---|---|---|

Classes:
`PRODUCT_DECISION`, `PRODUCT_CONFIRMATION`, `TECHNICAL_CONSEQUENCE`, `ALREADY_DECIDED`

`ALREADY_DECIDED` requires a contract reference.

## Technical consequences

## Scope recommendation

## Result

`ENGINEERING_READY: YES | NO`
