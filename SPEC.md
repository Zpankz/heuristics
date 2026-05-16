# SPEC

**Heuristics Planning Methodology — Version 0.1 (Initial)**

This document is the canonical, relatively stable specification of the Heuristics generative planning methodology. It defines the core concepts, phases, gates, artifacts, and contracts that any implementation (Claude Code skill, Grok skill, future variants) must honor.

Implementations may add harness-specific UX, automation, or integration sugar, but they must not violate the rules below without a corresponding update to this spec.

---

## 1. Core Definitions

### 1.1 Minimally Viable Architecture (MVA)
The smallest runnable system that exercises the specific architectural seams whose correct shape is currently uncertain. The MVA is intentionally imperfect and is created for the explicit purpose of heuristic discovery. It is planning debt, not product debt.

### 1.2 Heuristic
An empirical rule, invariant, boundary, or failure mode that was discovered through stress on an MVA and has clear causal evidence from one or more iteration cycles. A heuristic is not a hypothesis; it is a post-experience observation with traceable backing.

### 1.3 Governance Layer
The synthesized artifact that becomes the source of truth for any subsequent rebuild. It contains at minimum:
- Orchestration specification (coordination model, state machines, event contracts, saga/compensation boundaries)
- Experience-backed Architecture Decision Records (ADRs)
- Observability governance (required signals, alertable conditions, correlation rules)
- Failure mode taxonomy (real modes observed, with blast radius, detection, and recovery)
- Stable interface contracts and cross-cutting invariants

The governance layer must be traceable: every major claim must reference specific iteration cycles and heuristics.

### 1.4 Sacrificial Principle
The MVA must be explicitly deprecated before the rebuild plan is generated. No production code may be derived from the MVA implementation itself — only from the governance layer.

---

## 2. The H0–H5 Phase Model

The methodology consists of six phases that together constitute the complete "plan phase."

### H0 — Framing & MVA Co-Definition
**Purpose:** Establish a shared, explicit contract for the probe.

**Required Outputs:**
- `mva-spec.md` containing:
  - 3–7 named architectural uncertainties being probed
  - Explicit "Known Technical Debt & Simplifications" list (persistence, error handling, security, observability, deployment, etc.)
  - Module inventory with primary contracts
  - Minimum Viable Stress criteria (measurable)

**Gate:** User (or stakeholder) must explicitly agree to the scope and debt list before H1 begins.

### H1 — Scaffold Implementation
**Purpose:** Produce a working, executable MVA with clear module boundaries.

**Constraints:**
- Modularity is prioritized over elegance or performance.
- The entire MVA must be marked as sacrificial.
- Primary happy paths defined in the mva-spec must execute.

### H2 — Modular Iteration & Heuristic Mining
**Purpose:** Generate the empirical evidence.

**Cycle:** Evolve → Stress/Evaluate → Debug → Refactor → Capture

**Minimum Viable Stress Gate (strict — blocks progression to H3):**
- At least one non-trivial distributed or cross-module failure has been experienced, diagnosed, and mitigated through iteration.
- At least one cross-cutting concern (retry, idempotency, compensation, ordering, observability, rate limiting, etc.) has been forced to evolve under pressure, revealing previously invisible coupling.
- The iteration log contains 5–15 concrete heuristics with traceable evidence.
- The team/agent can articulate which architectural seams have "shown their true shape."

Happy-path-only iteration for more than 2–3 cycles without deliberate failure injection violates the spec.

### H3 — Governance Layer Synthesis
**Purpose:** Convert lived experience into a durable, reusable specification.

**Required Outputs:**
- `governance/governance-layer.md` (or split equivalent) containing all sections defined in Section 1.3 above.
- Every major decision must be traceable to specific H2 cycles and heuristics.
- "Day One Regret" observability retrospective must be non-empty and specific.

### H4 — Sacrificial Throw & Rebuild Planning
**Purpose:** Formally retire the MVA and produce a high-fidelity rebuild plan.

**Required Rituals & Outputs:**
- `mva/DEPRECATED.md` explicitly stating that the MVA is no longer a source of truth.
- `rebuild-plan.md` whose sole specification inputs are the governance layer (plus the original problem statement for context only).

The rebuild plan must be executable by a competent agent who has never seen the MVA code.

### H5 — Rebuild Execution
**Purpose:** Construct the production-grade system from the governance layer.

**Characteristics of a correct H5:**
- Observability and governance concerns are addressed from the start (not retrofitted).
- Failure modes have documented, tested recovery paths.
- No "ghost code" from the MVA survives without explicit re-justification against the governance layer.

---

## 3. Artifact Contracts

All implementations must produce artifacts that are consistent with the templates in `templates/` (or demonstrably superior equivalents that preserve the same information density and traceability).

Key artifacts:
- `mva-spec.md`
- `iteration-log.md` (living)
- `heuristics-catalog.md` (curated subset)
- `governance-layer.md` (and sub-documents)
- `rebuild-plan.md`
- `mva/DEPRECATED.md`

---

## 4. Traceability & Evidence Requirements

- No heuristic may be promoted to the governance layer without a traceable cycle in the iteration log.
- No architectural decision in the governance layer may lack real (as opposed to hypothetical) evidence from MVA stress.
- The "Minimum Viable Stress" gate is non-negotiable for any claim of methodological correctness.

---

## 5. Scope and Anti-Scope

**Heuristics is appropriate when:**
- The correct orchestration model, state machine boundaries, or cross-cutting governance contracts are genuinely uncertain.
- The cost of discovering the wrong shape in production is high.
- The cost of a small throwaway MVA is acceptable.

**Heuristics is explicitly not appropriate for:**
- Incremental work on well-understood patterns (use speculative planning tools).
- Pure product definition or requirements discovery (use brainstorming/requirements tools first).
- Situations where the political or time cost of building even a small MVA is prohibitive.

---

## 6. Evolution of This Spec

This specification (v0.1) will be updated when real usage across multiple projects demonstrates that:
- A phase gate is systematically too weak or too strong.
- A required artifact section is consistently missing critical information.
- A new class of cross-cutting concern or governance element has emerged that is not yet covered.

Changes to this SPEC.md require corresponding updates to `SKILL.md`, templates, phase gates reference, and both Claude and Grok skill implementations.

---

**Status:** v0.1 — Initial public definition (May 2026)