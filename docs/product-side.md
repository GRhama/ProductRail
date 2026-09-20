# Product Side

The Product side is designed to work even when the PM does not have repository access.

## Goal

Turn an ambiguous request into explicit behavior with the minimum stakeholder decision load.

## Meeting model

- start with what is already known;
- surface only blocking decisions;
- keep questions atomic;
- allow free-form answers;
- treat stakeholder speech as evidence;
- extract proposed interpretations from long answers;
- require human confirmation before marking an interpretation `RESOLVED`;
- identify contradictions;
- re-grill only unresolved delta.

## Product-ready test

Ask:

> Could two competent engineers read this contract and implement materially different product behavior?

If yes, the Product contract probably still has an important gap.

Apply the complete `PRODUCT_READY` and `STORIES_READY` contracts from `docs/workflow.md`. Persist every relevant transition.
