---
lat:
  require-code-mention: false
---

# MVA — {{PROJECT_OR_FEATURE_NAME}}

**Status:** In Progress | Validated | Deprecated
**Started:** {{DATE}}
**Last Updated:** {{DATE}}
**Owner:** {{AGENT_OR_PERSON}}

*This document follows `lat.md` conventions. Every section opens with a leading paragraph that establishes its identity (≤250 chars ideal). This is a living journal — append honestly, including dead ends and pivots.*

---

## Purpose

This is the living journal of the iterative discovery process for `{{PROJECT_OR_FEATURE_NAME}}`. It records what was tried, what happened, what was learned, and what changed — cycle by cycle — until a working Minimally Viable Architecture is confirmed.

---

## Context & Starting Hypothesis

Establishes the problem framing and the first concrete guess at a working architecture before any iteration begins.

**Problem context:**

{{BRIEF_DESCRIPTION_OF_THE_ARCHITECTURAL_PROBLEM}}

**Initial hypothesis:**

{{INITIAL_HYPOTHESIS}}

---

## Iteration Log

Each significant cycle of work is recorded below as a numbered section. Add cycles forward; never delete or revise past cycles. Honest recording of failures and reversals is required.

---

### Cycle 001 — {{SHORT_TITLE_OR_FOCUS}} — {{DATE}}

#### Focus

What this cycle is attempting to answer, validate, or build. One or two sentences. State the specific uncertainty being reduced.

{{CYCLE_001_FOCUS}}

#### What Was Tried

Concrete actions taken: code written, configs changed, experiments run, integrations attempted. Be specific.

- {{ACTION_1}}
- {{ACTION_2}}

#### What Happened

Observed outcomes — successes, failures, surprises, errors. Raw and factual. Do not interpret here.

- {{OUTCOME_1}}
- {{OUTCOME_2}}

#### What Was Learned

Interpretation of outcomes. What does this reveal about the architecture, the problem, or the hypothesis? What is now known that was not known before?

{{LEARNING}}

#### Changes Made

Concrete mutations to the architecture, design decisions, or process resulting from this cycle.

- {{CHANGE_1}}

---

### Cycle 002 — {{SHORT_TITLE_OR_FOCUS}} — {{DATE}}

#### Focus

{{CYCLE_002_FOCUS}}

#### What Was Tried

- 

#### What Happened

- 

#### What Was Learned

{{LEARNING}}

#### Changes Made

- 

---

## Current State of the MVA

Snapshot of the architecture as it stands after the most recent completed cycle. Updated after each cycle that produces a meaningful change.

**Working shape:**

{{DESCRIPTION_OF_CURRENT_ARCHITECTURE}}

**Stabilized modules or components:**

- 

**Active unknowns (original from Frame):**

- 

**Emergent unknowns (discovered during Iterate):**

- {{Unknown}} `[EMERGENT — Cycle N]`

**Technical debt accepted in this MVA:**

- 

---

## Decision Log

Major architectural decisions made during iteration. Record the decision, why it was made, and whether it held.

| Decision | Rationale | Date | Status |
|----------|-----------|------|--------|
| {{DECISION}} | {{WHY}} | {{DATE}} | Accepted / Reversed |

---

## Extracted Heuristics

Reusable truths that transcend this specific problem. Each heuristic emerged from a specific cycle but applies beyond this MVA. These survive deletion and may inform future MVAs or execution.

| Heuristic | Discovered In | Applicable To |
|-----------|---------------|---------------|
| {{Reusable truth}} | Cycle {{N}} | {{Domain or pattern where this applies}} |

---

## Criteria for MVA Completion

This section defines the exit gate for the MVA phase. Completion is not declared on feel — it requires evidence against each criterion. These criteria are derived from Phase 1 framing: the MVA is complete when the minimum viable stress has been applied and a stable working shape has emerged.

- [ ] The core architectural seams have been stressed under realistic load or use conditions (Phase 1 minimum viable stress criterion).
- [ ] At least one failure mode has been encountered and resolved or explicitly accepted.
- [ ] The current implementation demonstrates the architecture working end-to-end.
- [ ] We can articulate clearly what worked, what didn't, and why the current shape holds.
- [ ] Validated learnings are sufficient to decompose into spec-based output without locking in fragile assumptions.
- [ ] All emergent uncertainties are either resolved or explicitly deferred with rationale.

**Current assessment:**

{{NOTES}}

---

## Next Steps

What will be attempted in the next cycle, or what formal documentation work begins once the MVA is declared complete.

{{WHAT_WE_PLAN_TO_DO_NEXT}}
