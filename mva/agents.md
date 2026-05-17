# Agent Instructions — MVA Skill

This file defines how agents behave when executing the MVA skill. It is the behavioral contract: what to do, what to enforce, and what to refuse.

## Reading Order

When this skill is invoked, read in this sequence:

1. **[[SKILL.md]]** — What the skill does and how to invoke it.
2. **[[spec.md]]** — The methodology specification (invariants, constraints, guarantees).
3. **[[agents.md]]** (this file) — Behavioral contract during execution.
4. **[[templates/mva.md]]** — The journal template you'll use during iteration.

Do not skip `spec.md`. It contains the invariants that constrain every decision you make during execution.

## Behavioral Rules

### During Phase 1 (Frame)

- Ask questions. Do not assume you understand the uncertainties.
- Push back on scope inflation. If the MVA would take more than a few days to build, it's too large.
- Require explicit stress criteria. "We'll know it works" is not measurable.
- Do not proceed until the user actively confirms scope. "Looks good" is insufficient.

### During Phase 2 (Iterate)

- Journal every cycle. No exceptions. If you built or changed something, record it.
- Write disposable code. Do not add production concerns (CI, comprehensive tests, auth, observability) unless they directly stress an uncertainty.
- Each cycle must have all five fields: Focus, What Was Tried, What Happened, What Was Learned, Changes Made.
- Extract heuristics when you notice reusable truths. These transcend the current problem.
- Register emergent uncertainties explicitly. When building reveals a new unknown not in the Frame, add it to the uncertainty list with `[EMERGENT — Cycle N]` tag.
- If emergent uncertainties dominate (>50% of active list), suggest re-framing. This is not failure — it's discovery working correctly.
- Monitor for diminishing returns using concrete signals: last 2 cycles confirmatory-only, stress criteria pass without changes, heuristic extraction yields restatements, cannot articulate next cycle's target.

### During Phase 3 (Formalize)

- Work from the journal only. Do not introduce requirements, components, or guidance from memory or general knowledge unless marked `[UNVERIFIED]`.
- Trace every claim to a cycle. Use `[Cycle N]` notation.
- Produce all six outputs: `spec.md`, `design.md`, `lat.md`, `tools.md`, `goal.md`, `agents.md` for the target project.
- Flag gaps. If the journal doesn't cover something that feels important, mark it `[UNVERIFIED]` rather than filling from imagination.

### During Phase 4 (Delete)

- Extract heuristics table from journal into `lat.md` evolution vectors before deletion.
- Delete the journal file. Do not archive it, do not keep it "just in case."
- Delete scaffold code. Do not refactor it into the real build.
- Verify no dangling references to deleted artifacts remain in output documents.

## What to Refuse

- Writing any output document (spec, design, lat, tools, goal, agents) before the journal is complete.
- Treating MVA scaffold as production code (adding comprehensive tests, CI, docs to it).
- Skipping journal entries ("I'll record this later").
- Continuing iteration when the user wants to stop for non-evidence reasons ("I'm tired of this").
- Deleting the journal before formalization is complete.

## What to Enforce

- The lifecycle order: Frame → Iterate → Formalize → Delete. No shortcuts.
- Journal discipline: every cycle, every field, every time.
- Traceability: every formalized claim traced to evidence.
- Scope minimalism: the MVA stays small and focused on uncertainties.
- Sacrificial intent: the MVA is temporary from its first line of code.

## Integration with Other Skills

When MVA is active:
- **Planning skills** are suspended. MVA replaces upfront planning with empirical discovery.
- **TDD** is used during scaffold building. Tests become evidence in the journal.
- **Code review** is relaxed for MVA code (disposable) but restored for post-MVA execution.
- **hermes /goal** can execute the `goal.md` produced by this skill directly.

## State Tracking

The skill maintains state via the journal file in the target project. Phase is determined by journal state:

| Journal State | Current Phase |
|---------------|---------------|
| Does not exist | Pre-Frame or Post-Delete |
| Exists, no cycles | Frame (just started) |
| Exists, cycles present, uncertainties unresolved | Iterate |
| Exists, all uncertainties resolved | Ready to Formalize |
| Deleted, output docs exist | Complete |

Use `/mva status` to report current phase based on journal state.
