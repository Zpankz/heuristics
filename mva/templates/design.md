---
lat:
  require-code-mention: false
---

# DESIGN — {{PROJECT_OR_FEATURE_NAME}}

**Version:** {{X.Y}}  
**Status:** Draft | Stable | Deprecated  
**Derived from:** MVA journal completed on {{DATE}} ({{EXTRACTED_FROM_MVA_CYCLE}})  
**Last Updated:** {{DATE}}

*This document follows lat.md conventions. Every section opens with a leading paragraph that establishes its identity (≤250 chars ideal). This document captures HOW the system is built — the implementation approach, structural decisions, and technical patterns. For WHAT the system must do, see `SPEC.md`.*

---

## Overview

This design document formalizes the implementation architecture extracted from the completed MVA journal. It answers HOW the system is constructed — components, patterns, data flow, and operational posture — not WHAT it must do (that is `SPEC.md`'s domain).

It was produced by decomposing the validated `MVA.md` after iteration was complete. Every claim here traces to evidence from at least one MVA cycle. Speculative content must be marked as such.

---

## Design Goals & Constraints

Design goals and constraints are not invented here — they are distilled from MVA evidence. Each goal cites the cycle that validated it.

**Primary Design Goals:**

| Goal | MVA Evidence | Cycle |
|------|-------------|-------|
| {{GOAL_STATEMENT}} | {{EVIDENCE_FROM_JOURNAL}} | {{EXTRACTED_FROM_MVA_CYCLE}} |

**Hard Constraints:**

- 

**Guiding Principles (from MVA learnings):**

- 

---

## System Design

The system design section describes the structure and responsibilities of each component as they emerged from the MVA process — not as they were anticipated.

### Component Breakdown

| Component | Responsibility | Discovered In |
|-----------|----------------|---------------|
| {{COMPONENT_NAME}} | {{RESPONSIBILITY}} | {{EXTRACTED_FROM_MVA_CYCLE}} |

**Interaction Notes:**

{{HOW_COMPONENTS_INTERACT_AND_KEY_INTEGRATION_BOUNDARIES}}

---

## Key Technical Patterns & Approaches

Each pattern below was selected or confirmed during MVA iteration. Patterns not validated against real execution are not listed here.

### {{PATTERN_OR_APPROACH_NAME}}

{{CONCISE_IDENTITY_OF_THIS_PATTERN_AND_WHY_IT_IS_PRESENT}}

**How it works:**

{{MECHANISM_DESCRIPTION}}

**Why it was chosen (validated in MVA cycle {{EXTRACTED_FROM_MVA_CYCLE}}):**

{{EVIDENCE_BASED_RATIONALE}}

**Implementation notes:**

{{DETAILS_GOTCHAS_AND_EDGE_CASES}}

---

## Data Flow & State Management

Data flow describes how information moves through the system at runtime. State management describes where mutable state lives and how it is controlled.

{{DESCRIPTION_OF_HOW_DATA_MOVES_THROUGH_THE_SYSTEM}}

**State ownership:**

{{WHERE_STATE_LIVES_AND_WHAT_OWNS_IT}}

**Flow diagram (if applicable):**

{{ASCII_OR_MERMAID_DIAGRAM_OR_DELETE_SECTION}}

---

## Error Handling, Resilience & Observability

This section captures the failure-mode design — what the system does when things go wrong, and how operators can see into it. Failure modes discovered during MVA iteration should be listed explicitly.

**Failure modes discovered in MVA:**

- 

**Error handling approach:**

{{HOW_ERRORS_ARE_CAUGHT_PROPAGATED_AND_SURFACED}}

**Resilience mechanisms:**

{{RETRY_FALLBACK_CIRCUIT_BREAKING_OR_GRACEFUL_DEGRADATION_STRATEGIES}}

**Observability:**

{{LOGGING_METRICS_TRACING_AND_ALERTING_APPROACH}}

---

## Security, Performance & Operational Considerations

Operational concerns that are not functional requirements but constrain how the system may be built or deployed.

**Security:**

- 

**Performance:**

- 

**Operational:**

- 

---

## Open Implementation Questions

Questions that remain unresolved after formalization. Each item should either be answered before the GOAL phase begins or explicitly accepted as a known unknown.

- 

---

---

**Related documents:** [[spec.md]] (WHAT) · [[lat.md]] (WHY + graph) · [[tools.md]] (dependencies) · [[goal.md]] (execution contract) · [[agents.md]] (behavioral rules)
