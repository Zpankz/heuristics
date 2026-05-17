# GOAL — {{PROJECT_OR_FEATURE_NAME}}

This document is the executable goal contract for {{PROJECT_OR_FEATURE_NAME}}. It is synthesized from a completed MVA journal, DESIGN.md, and SPEC.md. An agent or person beginning work from this document alone should have sufficient orientation to proceed without consulting the archived MVA scaffold.

Conventions follow lat.md style: every section opens with a leading paragraph establishing its identity before elaborating with structure.

**Synthesized by:** {{AGENT_OR_PERSON}}
**Date:** {{DATE}}
**Source documents:** MVA.md (archived), DESIGN.md, SPEC.md

---

## Aspiration

State the core purpose of this work in one or two sentences. This is not a scope boundary — it is the animating intent that should survive every tradeoff decision made during execution.

{{Describe the single most important thing this work exists to achieve and why it matters now.}}

---

## Success Vision

A concrete description of the world after this work is complete. Success Vision is written in present tense as if the work is done — it makes the endpoint legible so execution decisions can be evaluated against it.

{{Describe what the system does, how it behaves, and what is different about the world after this goal is achieved. Include the user or system perspective, not just the implementation perspective.}}

**The work is done when:**

- {{Criterion 1 — measurable, observable, not open to interpretation}}
- {{Criterion 2}}
- {{Criterion 3}}

---

## Key Learnings from MVA Phase

This section records what the MVA journal revealed that directly shaped this GOAL. Each entry is grounded in a specific MVA cycle — not post-hoc analysis. These learnings are the reason this GOAL is structured the way it is.

Entries here are empirical findings, not design opinions. They carry evidential weight and should not be overridden during execution without recording a reasoned exception.

### Learning 1 — {{Short Title}}

**Discovered in:** MVA Cycle {{N}}

{{What the MVA revealed. What assumption was wrong or confirmed. What changed as a result.}}

**Implication for this GOAL:** {{What constraint, decision, or approach this learning imposes on the rebuild.}}

### Learning 2 — {{Short Title}}

**Discovered in:** MVA Cycle {{N}}

{{What the MVA revealed.}}

**Implication for this GOAL:** {{Constraint or decision.}}

### Learning 3 — {{Short Title}}

**Discovered in:** MVA Cycle {{N}}

{{What the MVA revealed.}}

**Implication for this GOAL:** {{Constraint or decision.}}

---

## Anticipated Difficulties & Risks

This section names the known hard parts before execution begins. Every entry is grounded in what the MVA actually revealed — not speculation about what might go wrong. Entries are actionable: each risk has a named mitigation.

### Risk 1 — {{Short Title}}

**Grounded in:** MVA Cycle {{N}} / {{Specific observation}}

**Why it is hard:** {{What makes this genuinely difficult based on MVA evidence.}}

**Mitigation:** {{Concrete approach to reduce or contain this risk during execution.}}

### Risk 2 — {{Short Title}}

**Grounded in:** MVA Cycle {{N}} / {{Specific observation}}

**Why it is hard:** {{What makes this genuinely difficult.}}

**Mitigation:** {{Concrete approach.}}

### Risk 3 — {{Short Title}}

**Grounded in:** MVA Cycle {{N}} / {{Specific observation}}

**Why it is hard:** {{What makes this genuinely difficult.}}

**Mitigation:** {{Concrete approach.}}

---

## Scope & Non-Goals

Scope defines what is explicitly included. Non-Goals define what is explicitly excluded — naming them prevents scope creep and resolves ambiguity during execution without escalation.

**In scope:**

- {{Capability or concern this work includes}}
- {{Capability or concern this work includes}}
- {{Capability or concern this work includes}}

**Not in scope (non-goals):**

- {{What this work deliberately excludes and why — one sentence per item}}
- {{What this work deliberately excludes and why}}
- {{What this work deliberately excludes and why}}

---

## Execution Guidance

This section gives an agent or person enough orientation to begin work from this document alone. It covers primary approach, recommended workflow, and working memory conventions.

### Primary Approach

The overall strategy for executing this goal, derived from DESIGN.md and grounded in MVA learnings. This is not a step-by-step plan — it is the architectural and methodological stance that should govern individual decisions.

{{Describe the primary technical approach: what is being built, how it is decomposed, what constraints govern implementation choices, and what tradeoffs are already resolved.}}

**Key architectural decisions already made:**

| Decision | Rationale | MVA Evidence |
|----------|-----------|--------------|
| {{Decision}} | {{Why}} | {{Cycle N: what was observed}} |
| {{Decision}} | {{Why}} | {{Cycle N: what was observed}} |
| {{Decision}} | {{Why}} | {{Cycle N: what was observed}} |

### Recommended Workflow

The preferred sequence of work given the dependencies, risks, and learnings recorded in this document. Phases should be ordered to surface remaining uncertainty early and defer stable work until foundations are proven.

**Phase 1 — {{Phase Name}}**
{{What to do, what to produce, what signal indicates this phase is complete.}}

**Phase 2 — {{Phase Name}}**
{{What to do, what to produce, what signal indicates this phase is complete.}}

**Phase 3 — {{Phase Name}}**
{{What to do, what to produce, what signal indicates this phase is complete.}}

**When blocked:** {{How to handle ambiguity or unexpected findings — escalate, record, or apply a named heuristic.}}

### Working Memory & Artifacts

Where to keep notes, decisions, and intermediate outputs during execution. Consistent artifact hygiene prevents re-discovery of already-resolved questions.

**Decision log:** Record architectural deviations from this GOAL and their rationale in `DECISIONS.md` alongside this file. Do not alter GOAL.md retrospectively.

**Intermediate artifacts:** {{Where to place drafts, test results, spike outputs — naming convention and location.}}

**Completion artifact:** {{What document or test suite represents the terminal state of this work.}}

---

## Verification & Quality Bar

Measurable criteria that determine whether the work meets the standard implied by the Success Vision. These are not aspirational — they are the minimum bar for declaring the goal complete.

### Functional Verification

- [ ] {{Specific behavior or output that can be observed or tested}}
- [ ] {{Specific behavior or output}}
- [ ] {{Specific behavior or output}}

### Non-Functional Verification

- [ ] {{Performance, reliability, or security criterion with a numeric threshold where applicable}}
- [ ] {{Non-functional criterion}}
- [ ] {{Non-functional criterion}}

### Process Verification

- [ ] Key Learnings from the MVA phase have not been violated without a recorded exception in DECISIONS.md
- [ ] Non-goals listed in this document were not silently in-scoped
- [ ] {{Additional process check specific to this project}}

---

## Final Notes & Motivation

This section is optional but encouraged. It records context that does not fit elsewhere — the why behind the why, the history that explains why this problem is being solved this way, and any human or organizational context that should survive into execution.

{{Write anything that would help a future agent or person understand why this goal matters, why this approach was chosen over alternatives, and what to watch out for that is not captured elsewhere. This section should feel honest, not formal.}}

---

**Related documents:** [[spec.md]] (requirements) · [[design.md]] (architecture) · [[lat.md]] (decision graph) · [[tools.md]] (dependencies) · [[agents.md]] (behavioral rules)
