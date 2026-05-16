---
lat:
  require-code-mention: false
---

# MVA

**MVA.md — The Living Journal of Architectural Discovery**

This document follows `lat.md` conventions. Every section begins with a leading paragraph.

---

## Role in the Methodology

`MVA.md` is the primary working document during the discovery phase of the MVA heuristic.

It functions as a living journal in which the agent and user record what was tried, what succeeded, what failed, and how architectural understanding evolved while building a real, runnable Minimally Viable Architecture.

Unlike `SPEC.md` or `DESIGN.md`, `MVA.md` is intentionally temporary and is deleted once its purpose is fulfilled.

---

## Lifecycle Position

`MVA.md` is created and maintained first.

Only after it demonstrates a validated, working architecture does the team decompose its learnings into the more permanent `DESIGN.md` and `SPEC.md`.

These three documents are then used together to produce `GOAL.md`.

After `GOAL.md` is finalized, `MVA.md` is removed.

---

## How to Use This Document

Copy the template from `templates/MVA.md` into the root of a new project when beginning work on a high-uncertainty architectural problem.

Add new cycles or phases as iteration progresses. Record both positive and negative outcomes honestly.

Treat this file as the single source of truth for what actually happened during the MVA construction process.

---

## Production Usage

When applying the MVA heuristic:

- Begin writing `MVA.md` immediately as work starts.
- Update it continuously throughout iteration.
- Do not attempt to formalize `DESIGN.md` or `SPEC.md` until the journal indicates that a stable MVA has been achieved.

This discipline ensures that formal documentation is grounded in real experience rather than speculation.

---

## Relationship to Other Documents

- `AGENTS.md` and `SKILL.md` provide the instructions and adaptive logic for maintaining `MVA.md`.
- `LAT.md` maps concepts discovered in various `MVA.md` journals across projects.
- `SPEC.md` and `DESIGN.md` are the direct technical descendants of a completed `MVA.md`.
- `GOAL.md` is synthesized from a completed `MVA.md` together with its derived `SPEC.md` and `DESIGN.md`.

---

*This document is the production-ready definition of `MVA.md`. For the detailed template with variables and iterative structure, see `templates/MVA.md`.*