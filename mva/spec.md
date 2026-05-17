# MVA Methodology Specification

This document specifies the MVA heuristic as a formal methodology. It defines the invariants, constraints, and guarantees that any implementation of the skill must honor. Read [[SKILL.md]] first for overview; this file provides the authoritative rules.

## Foundational Axioms

Three axioms constrain the entire methodology. Violating any one produces unreliable outputs regardless of how faithfully the process is followed.

**A1: Empiricism over speculation.** Every claim in formalized output must trace to evidence from a running system. Claims without provenance are speculative and must be marked `[UNVERIFIED]`.

**A2: Sacrificial intent.** The MVA exists to be discarded. Production concerns (auth, observability, error handling, deployment) are intentionally simplified. Code quality is irrelevant; learning quality is everything.

**A3: Formalization follows discovery.** Output documents are decomposed from a completed journal. They are never composed from imagination or memory. The journal is the source of truth until formalization is complete.

## Phase Specifications

### Phase 1: Frame

**Purpose:** Define what the MVA needs to stress-test.

**Preconditions:**
- User has identified a problem with architectural uncertainty
- No existing spec-based output covers this uncertainty

**Required outputs:**
- 3–7 architectural uncertainties, explicitly named and ranked by risk
- MVA scope bounded to hours–days of build effort
- Intentional simplifications list (what the MVA skips and why)
- Module boundaries named at a level allowing independent evolution
- Minimum viable stress criteria (measurable conditions the MVA must survive — may be provisional and refined during Iterate)

**Exit criteria:** User explicitly confirms "this scope is sufficient to discover what we need to know."

**Invariants:**
- Scope must be genuinely minimal. If MVA scope ≈ full product, reframe.
- Simplifications must be explicit, not vague. "Simplified auth" is insufficient; "hardcoded single user, no token validation" is explicit.
- Stress criteria must be measurable, not aspirational. However, provisional criteria are acceptable when full measurement requires partial building — these refine during Phase 2.

### Phase 2: Iterate

**Purpose:** Build, stress, and journal until uncertainties are resolved.

**Preconditions:**
- Phase 1 exit criteria met
- Journal file created from [[templates/mva.md]]

**Per-cycle requirements:**
- Each cycle records: Focus, What Was Tried, What Happened, What Was Learned, Changes Made
- Cycles are numbered sequentially and dated
- Heuristics (reusable truths) are extracted when they emerge
- Emergent uncertainties (unknowns discovered during building) are registered explicitly and added to the uncertainty list with provenance

**Emergent uncertainty protocol:**
When iteration reveals a new architectural unknown not identified during Frame:
1. Record it in the journal cycle where it emerged
2. Add it to the uncertainty list with tag `[EMERGENT — Cycle N]`
3. Rank it relative to existing uncertainties
4. If it invalidates or subsumes a Frame-phase uncertainty, note the supersession

**Re-framing trigger:**
If emergent uncertainties substantially change the MVA's direction (>50% of active uncertainties are emergent), pause iteration and re-frame. This is not a failure — it is the discovery process working correctly.

**Exit criteria (ALL must hold):**
- Every uncertainty (original + emergent) has an evidence-based answer OR is explicitly deferred with rationale
- New iterations produce diminishing returns (no new discoveries in last 2+ cycles)
- Journal tells a coherent story of discovery from start to resolution

**Diminishing returns signals** (concrete indicators beyond "no new discoveries"):
- Last 2 cycles produced only confirmatory evidence, no corrections or surprises
- Stress criteria pass without requiring code changes
- Heuristic extraction yields only restatements of existing heuristics
- Agent or user cannot articulate what the next cycle would target

**Invariants:**
- Never iterate without journaling. Unjournaled work cannot be formalized.
- Never stop because the team is tired. Stop because uncertainties are resolved.
- Never stop because the work is interesting. Stop when returns diminish.
- Never fix MVA bugs for production quality — record them as evidence.

### Phase 3: Formalize

**Purpose:** Decompose the completed journal into spec-based project output.

**Preconditions:**
- Phase 2 exit criteria met
- Journal is complete and coherent

**Required outputs:**

| Document | Derived From | Contains |
|----------|-------------|----------|
| `spec.md` | Journal cycles → requirements | What the system must do: functional/non-functional requirements, contracts, verification criteria |
| `design.md` | Journal cycles → architecture | How the system is built: components, patterns, data flow, error handling |
| `lat.md` | Journal cycles → structural relationships | Architecture trace: component graph, decision graph, constraint map, module boundaries |
| `tools.md` | Journal cycles → dependencies | Tool contract: runtime/build deps, external services, environment config |
| `goal.md` | spec + design + lat synthesis | Executable contract: aspiration, approach, workflow, verification bar |
| `agents.md` | Execution patterns | Agent behavioral instructions for goal execution |

**Traceability rule:** Every requirement in `spec.md`, every component in `design.md`, and every guidance in `goal.md` must reference the journal cycle where the evidence was discovered. Use format: `[Cycle N]` or `[Cycles N, M]`.

**Unverified content rule:** Any claim that cannot be traced to journal evidence must be marked `[UNVERIFIED]` and flagged for validation during execution.

**Exit criteria:**
- All six output documents exist (spec, design, lat, tools, goal, agents)
- No unmarked speculative claims remain
- Documents are internally consistent (spec requirements covered by design components, lat traces decisions, tools enumerates deps, goal references all)

### Phase 4: Delete

**Purpose:** Remove sacrificial artifacts. The spec-based output is now the single source of truth.

**Preconditions:**
- Phase 3 exit criteria met

**Required actions:**
- Extract heuristics table from `mva.md` into `lat.md` evolution vectors or a project-level heuristics registry (these survive deletion — they transcend this specific problem)
- Delete `mva.md` from target project
- Delete any scaffold code built during Phase 2
- Verify output documents are self-contained (no dangling references to deleted artifacts)

**Post-conditions:**
- Target project contains only: `spec.md`, `design.md`, `lat.md`, `tools.md`, `goal.md`, `agents.md`
- No `mva.md` exists
- No scaffold code exists

## Output Document Contracts

### spec.md

The specification answers: **what must the system do?**

Required sections:
- Problem statement (what architectural question was answered)
- Scope and non-goals (boundaries)
- Requirements (functional + non-functional, each traced to cycle evidence)
- Interface contracts (APIs, events, data shapes)
- Verification criteria (how to prove requirements are met)

### design.md

The design answers: **how is the system built?**

Required sections:
- Component breakdown (each component traced to cycle discovery)
- Technical patterns and approaches (with evidence of why chosen)
- Data flow and state management
- Error handling and resilience strategy
- Security and performance considerations

### lat.md

The architecture trace answers: **how do components relate and why were decisions made?**

Required sections:
- System identity (one-sentence architectural insight)
- Component graph (nodes and edges with cycle provenance)
- Decision graph (choices, alternatives rejected, evidence)
- Constraint map (discovered and inherited constraints)
- Module boundaries (validated independence evidence)
- Evolution vectors (structural affordances for growth)

### tools.md

The tool contract answers: **what dependencies does execution require?**

Required sections:
- Runtime dependencies (libraries, frameworks with versions)
- Build dependencies (dev tooling)
- External services (APIs, databases, infrastructure)
- Agent tool requirements (MCP tools, CLI commands)
- Environment configuration (variables, secrets)
- Compatibility constraints (version conflicts, platform requirements)

### goal.md

The goal answers: **what does the agent execute?**

Required sections:
- Aspiration (what success looks like)
- Key learnings from MVA (grounded insights that must inform execution)
- Execution guidance (approach, workflow, artifacts)
- Verification bar (measurable completion criteria)

### agents.md

The agents file answers: **how should agents behave during execution?**

Required sections:
- Reading order for project documents
- Behavioral constraints
- Workflow expectations
- Quality standards

## Constraints and Guarantees

**The skill guarantees:**
- Output is grounded in empirical evidence from a running system
- Speculative content is explicitly marked
- The lifecycle order (frame → iterate → formalize → delete) is never skipped or reversed — but re-framing within Iterate is a valid forward operation, not a violation
- Journal is never skipped or reconstructed post-hoc

**The skill does NOT guarantee:**
- The MVA will resolve all uncertainties (some problems need multiple MVAs)
- The formalized output is complete (execution may reveal gaps)
- The output is optimal (it's empirically grounded, not theoretically optimal)

## Failure Modes and Recovery

| Failure | Detection | Recovery |
|---------|-----------|----------|
| MVA scope too large | Build taking weeks, not days | Reframe: cut scope, pick top 2–3 uncertainties |
| Journal neglect | Cycles recorded without substance | Pause, retrospectively fill from memory, mark `[RECONSTRUCTED]` |
| Premature formalization | Spec/design written before exit criteria met | Delete premature output, continue iteration |
| Scaffold attachment | Resistance to deletion, "we'll just clean it up" | Enforce axiom A2. MVA code is never production code. |
| Diminishing returns unrecognized | Iteration continues past value | Review last 3 cycles — if no new uncertainties resolved, formalize |
