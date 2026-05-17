# SPEC — {{PROJECT_OR_FEATURE_NAME}}

Technical specification decomposed from a completed MVA journal. Every claim in this document traces to evidence from a real MVA cycle. Speculative content is explicitly flagged as such and must be resolved before the GOAL is finalized.

> **Convention.** This document follows lat.md conventions: each section opens with a leading paragraph (≤250 chars) establishing identity before lists or subsections. Extracted from MVA cycle: `{{EXTRACTED_FROM_MVA_CYCLE}}`. Date: `{{DATE}}`.

---

## Overview

This specification covers `{{PROJECT_OR_FEATURE_NAME}}`. It is the authoritative technical contract for the rebuild, derived exclusively from empirical findings in the companion MVA journal.

**Traceability requirement.** Every non-trivial claim in this document must reference the MVA cycle entry where it was discovered (e.g., `[Cycle 3]`). Claims without cycle references are speculative and must be marked `[UNVERIFIED]` pending evidence.

---

## Problem Statement

The core problem `{{PROJECT_OR_FEATURE_NAME}}` solves, stated precisely. One paragraph, grounded in what the MVA revealed — not what was assumed before it ran.

**What the MVA confirmed:**

- [CYCLE REF] Confirmed problem statement point one.
- [CYCLE REF] Confirmed problem statement point two.

**What the MVA ruled out:**

- [CYCLE REF] Assumption that did not survive contact with reality.

---

## Scope & Non-Goals

What this specification covers, and what it explicitly excludes. Exclusions are intentional decisions, not oversights — each should trace to a MVA finding or deliberate deferral.

### In Scope

- [CYCLE REF] Capability or boundary within scope.
- [CYCLE REF] Capability or boundary within scope.

### Non-Goals

| Non-Goal | Rationale | Deferred To |
|----------|-----------|-------------|
| Feature or concern excluded | Why it is out of scope | Future cycle / separate spec / never |
| Feature or concern excluded | Why it is out of scope | Future cycle / separate spec / never |

---

## Architecture

The structural shape of the system as discovered through MVA iteration. Not a design proposal — a formalization of what worked.

### High-Level Architecture

Narrative description of the system's structural shape in one short paragraph. Then a diagram or component list.

```
[Diagram or ASCII component map]
```

**Key boundaries identified [CYCLE REF]:**

- Boundary or interface name — responsibility and contract summary.
- Boundary or interface name — responsibility and contract summary.

### Key Components / Modules

Each component or module that survived MVA iteration and belongs in the rebuild.

| Component | Responsibility | Discovered In |
|-----------|---------------|---------------|
| `ComponentName` | What it does, single sentence | [Cycle N] |
| `ComponentName` | What it does, single sentence | [Cycle N] |

**Component notes:**

#### `{{COMPONENT_NAME}}`

Single-paragraph description: what it owns, what it exposes, what it must not do.

- **Inputs:** ...
- **Outputs:** ...
- **Invariants:** ...

### Data / State Model

The persistent data and runtime state the system manages. Defined from MVA observation, not upfront schema design.

**Entities:**

| Entity | Key Fields | Source |
|--------|-----------|--------|
| `EntityName` | field: type, field: type | [Cycle N] |

**State transitions [CYCLE REF]:**

- State → Trigger → Next state

---

## Technical Decisions & Rationale

Decisions that survived the MVA. Format is fixed: Decision, Evidence (journal reference), Rationale. Do not add decisions that were not tested in the MVA — mark them `[UNVERIFIED]`.

| Decision | Evidence (from journal) | Rationale |
|----------|------------------------|-----------|
| [CYCLE REF] Decision statement | What the cycle revealed | Why this decision follows |
| [CYCLE REF] Decision statement | What the cycle revealed | Why this decision follows |
| [UNVERIFIED] Decision statement | No cycle evidence yet | Hypothesized reason |

---

## Requirements & Contracts

Formal requirements derived from MVA findings. Divided into functional, non-functional, and interface contracts.

### Functional Requirements

Behaviors the system must exhibit, each traceable to a discovered need.

| ID | Requirement | Source |
|----|-------------|--------|
| F-01 | The system shall ... | [Cycle N] |
| F-02 | The system shall ... | [Cycle N] |

### Non-Functional Requirements

Quality attributes the rebuild must satisfy, with measurable thresholds where possible.

| ID | Attribute | Threshold | Source |
|----|-----------|-----------|--------|
| NF-01 | Performance | Metric and target | [Cycle N] |
| NF-02 | Reliability | Metric and target | [Cycle N] |
| NF-03 | Security | Constraint | [Cycle N] / deliberate |

### API / Interface Contracts

Precise definitions of boundaries exposed or consumed. Derived from what the MVA exercised.

#### `{{INTERFACE_OR_ENDPOINT_NAME}}`

Short description of what this interface is and who uses it.

```
Method / Signature / Protocol definition
```

**Preconditions:** ...
**Postconditions:** ...
**Error cases:** ...
**Discovered constraints [CYCLE REF]:** ...

---

## Verification & Success Criteria

How we will know the rebuild is correct. Criteria are observable and testable — not vague quality statements.

**Acceptance criteria:**

| Criterion | How to Verify | Derived From |
|-----------|--------------|--------------|
| Observable outcome | Test method or observable check | [Cycle N] |
| Observable outcome | Test method or observable check | [Cycle N] |

**Stress criteria carried forward from MVA Phase 1:**

- Criterion the MVA was designed to satisfy — pass/fail statement.

**Regression surface [CYCLE REF]:**

- Failure mode discovered in MVA that the rebuild must not reintroduce.

---

## Open Questions & Known Limitations

Uncertainties that remain after the MVA. These must be resolved or explicitly accepted before the GOAL is finalized.

### Open Questions

| # | Question | Blocking? | Owner |
|---|----------|-----------|-------|
| Q-01 | Question that needs resolution | Yes / No | — |
| Q-02 | Question that needs resolution | Yes / No | — |

### Known Limitations

Constraints or weaknesses the rebuild inherits or consciously accepts.

- **Limitation.** Description and why it is accepted rather than resolved.
- **Limitation.** Description and why it is accepted rather than resolved.

---

---

**Related documents:** [[design.md]] (HOW) · [[lat.md]] (WHY + graph) · [[tools.md]] (dependencies) · [[goal.md]] (execution contract) · [[agents.md]] (behavioral rules)
