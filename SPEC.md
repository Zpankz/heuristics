---
lat:
  require-code-mention: false
---

# SPEC

**MVA Heuristic Methodology Specification**

This document defines the formal rules, phases, and contracts of the MVA heuristic. It is the canonical reference that any implementation or usage must follow.

---

## Purpose

The specification exists to ensure consistency and quality when the MVA heuristic is applied across different problems and agent harnesses.

It separates stable methodology rules from implementation details and from the living, project-specific journals created during actual use.

---

## Core Definitions

### Minimally Viable Architecture

A Minimally Viable Architecture is the smallest runnable system capable of stressing the specific architectural uncertainties that motivated the engagement.

It is created explicitly for discovery and is always treated as temporary.

### MVA Journal

The `MVA.md` document functions as a living journal. It records the iterative process of building and validating the MVA, including successes, failures, and evolving understanding.

### Governance Layer

The governance layer is the durable output synthesized from a completed MVA journal. It contains the orchestration model, key decisions, observability requirements, and failure patterns that have been validated through real stress.

---

## The MVA Heuristic Phases

The methodology consists of a discovery phase followed by formalization and execution phases.

### Discovery Phase

During this phase the agent works with the user to build a real MVA while maintaining a living `MVA.md` journal.

The phase continues until the MVA demonstrates a working architecture and sufficient validated learnings exist.

### Formalization Phase

Once the MVA journal is complete, its contents are decomposed into `DESIGN.md` and `SPEC.md`.

These documents represent the stable technical truth extracted from the discovery process.

### Goal Synthesis Phase

`GOAL.md` is created from the combination of the completed `MVA.md`, `DESIGN.md`, and `SPEC.md`.

The MVA journal is then deleted.

### Execution Phase

The goal is executed with support from `LAT.md`, `DESIGN.md`, and `SPEC.md`.

`LAT.md` is finalized after `GOAL.md` exists but before execution begins.

---

## Key Rules

The MVA must be genuinely stressed before formalization begins.

`MVA.md` must be written progressively during iteration rather than summarized after the fact.

`DESIGN.md` and `SPEC.md` may only be created after a MVA has been validated through real use.

`GOAL.md` must incorporate both the aspiration and the hard-won practical learnings from the MVA phase.

---

## Relationship to Other Documents

This specification defines the rules. The actual content for any given problem lives in that problem's `MVA.md`, `DESIGN.md`, `SPEC.md`, and `GOAL.md`.

`AGENTS.md` and `SKILL.md` provide the operational instructions for following this specification.

`LAT.md` captures cross-project patterns and mappings derived from multiple completed MVA journals.

---

*This document is intentionally stable. Changes require strong evidence from multiple real MVA engagements.*