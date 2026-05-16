---
lat:
  require-code-mention: false
---

# GOAL

**Purpose of the MVA Heuristic**

This document states the fundamental purpose and long-term aspirations of the MVA heuristic.

---

## Core Aspiration

The MVA heuristic exists to make the discovery of correct software architecture a repeatable, evidence-based discipline rather than a high-variance act of speculation.

It achieves this by requiring practitioners to build a real, runnable Minimally Viable Architecture, record the journey honestly in a living journal, and only then produce formal technical documentation and executable goals.

---

## Success Vision

In the long term, the methodology produces systems whose architecture feels as if it was designed by someone who had already lived through its failure modes.

Agents and humans using the heuristic routinely generate `GOAL.md` documents that are both ambitious and grounded in validated practical experience.

The set of documents (`MVA.md`, `DESIGN.md`, `SPEC.md`, `GOAL.md`, `LAT.md`) becomes a recognized, high-signal pattern for tackling architectural uncertainty.

---

## Key Principles

`MVA.md` must be written progressively during real work, not summarized afterward.

Formal documentation (`DESIGN.md` and `SPEC.md`) is only created after a MVA has been validated through iteration.

`GOAL.md` must carry forward both clear aspiration and the specific, hard-won learnings from the MVA phase.

All documents follow `lat.md` conventions to maximize agent navigability and long-term knowledge retention.

---

## Scope

The heuristic focuses on problems with genuine architectural uncertainty, especially those involving orchestration, distributed state, cross-cutting governance, or domains without strong local precedent.

It is explicitly not intended for incremental work on well-understood patterns.

---

*This goal is realized every time a practitioner completes a high-quality `MVA.md` journal, derives strong `DESIGN.md` and `SPEC.md` from it, and produces a `GOAL.md` that enables successful execution.*