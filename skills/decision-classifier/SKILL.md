# Skill: decision-classifier

## Purpose

Prevent unnecessary Product escalation by classifying gaps found during Engineering review.

## Classes

### PRODUCT_DECISION
A real missing behavior choice with more than one valid product outcome.

Action: return to Product.

### PRODUCT_CONFIRMATION
Behavior is strongly implied by the contract but ambiguity remains material.

Action: ask a short confirmation.

### TECHNICAL_CONSEQUENCE
Product behavior is clear; the remaining choice is implementation/architecture.

Action: Engineering decides and documents rationale.

### ALREADY_DECIDED
The answer already exists in the approved Product contract.

Action: cite and use the existing contract. Do not re-ask.

## Output

```text
ID:
CLASS:
EVIDENCE:
WHY:
ACTION:
CONTRACT_REFERENCE: required for ALREADY_DECIDED
```
