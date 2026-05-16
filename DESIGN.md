---
lat:
  require-code-mention: false
---

# DESIGN

**Technical Design for the MVA Heuristic**

This document describes the architectural and implementation design of the MVA heuristic skill and document system.

---

## Purpose

The design exists to explain how the various components and documents work together to support the MVA heuristic lifecycle.

It separates concerns between the living discovery process and the stable technical documentation produced afterward.

---

## High-Level Architecture

The system is organized around a clear temporal and conceptual separation between discovery and formalization.

### Discovery Layer

`MVA.md` serves as the active, iteratively updated journal during the construction and validation of a real architecture.

`SKILL.md` and `AGENTS.md` provide the instructions and adaptive logic that guide how the journal is maintained.

### Formalization Layer

After a MVA has been validated, its contents are decomposed into `DESIGN.md` and `SPEC.md`.

These documents capture the stable technical decisions and contracts that emerged from the MVA.

### Execution Layer

`GOAL.md` is synthesized from the completed MVA journal together with its derived `DESIGN.md` and `SPEC.md`.

`LAT.md` is maintained to provide navigable mappings for agents executing the goal.

---

## Document Relationships

`MVA.md` is the source of truth during discovery. It is intentionally discarded after formalization.

`DESIGN.md` and `SPEC.md` are the direct technical descendants of a validated `MVA.md`.

`GOAL.md` represents the executable contract and carries forward both the aspiration and the validated learnings.

`LAT.md` acts as the cross-project knowledge graph that supports long-term agent use of completed goals.

---

## Key Design Principles

The methodology deliberately separates the messy, high-learning phase of architectural discovery from the production of clean, stable documentation.

All core documents follow `lat.md` conventions to ensure they remain highly navigable by agents.

The temporary nature of `MVA.md` is a feature, not a bug. It protects the final `GOAL.md` from being contaminated by intermediate exploration.

---

*This design reflects the principle that high-quality architecture is best discovered through real iteration rather than pure speculation.*