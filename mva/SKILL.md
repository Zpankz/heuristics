---
name: mva
description: "Iterative architecture discovery through disposable builds. Use when facing genuine architectural uncertainty — multiple plausible designs, unfamiliar integrations, or problems where upfront specs would be immediately obsolete. Guides: frame unknowns → build/stress/journal → formalize into spec-based output → delete scaffold."
---

# MVA — Iterative Architecture Discovery Skill

This skill takes a problem with architectural uncertainty, guides iterative MVA construction with a living journal, then formalizes the output into a spec-based project structure. It replaces speculative planning with empirical discovery.

## Invocation

```
/mva                    # Start new MVA engagement
/mva status             # Show current phase and journal state
/mva iterate            # Record next iteration cycle
/mva formalize          # Decompose completed journal into spec-based output
/mva abort              # Abandon current MVA (with reason)
```

## What This Skill Does

When invoked on a new problem:

1. **Frames** the architectural uncertainty (3–7 unknowns, ranked by risk)
2. **Creates** a living journal from [[templates/mva.md]] in the target project
3. **Guides** iterative build-and-stress cycles, recording discoveries
4. **Recognizes** when iteration yields diminishing returns
5. **Formalizes** the journal into a spec-based project structure:
   - `spec.md` — What the system must do (from evidence)
   - `design.md` — How the system is built (component architecture)
   - `lat.md` — Architecture trace and decision graph
   - `tools.md` — Tool and dependency contract
   - `goal.md` — Executable contract for the real build
   - `agents.md` — Agent instructions for executing the goal
6. **Deletes** the MVA journal (sacrificial scaffold, heuristics preserved)

## The Core Inversion

Traditional planning: predict → specify → build → discover you were wrong.

MVA planning: **build small → stress → journal → formalize → build real.**

The insight: a small, intentionally disposable architecture stressed under real conditions reveals truths that no amount of upfront design can surface. The journal becomes raw material for rigorous specifications grounded in evidence rather than imagination.

## Skill Lifecycle

```
┌─────────────┐     ┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   FRAME     │────▶│   ITERATE   │────▶│  FORMALIZE   │────▶│   DELETE     │
│             │     │             │     │              │     │             │
│ Define      │     │ Build/stress│     │ Journal →    │     │ MVA gone    │
│ unknowns    │     │ + journal   │     │ spec-based   │     │ Spec-based  │
│             │     │ each cycle  │     │ output       │     │ repo remains│
└─────────────┘     └──────┬──────┘     └──────────────┘     └─────────────┘
                           │
                           ▼
                    (repeat until unknowns resolved)
```

## Phase Details

### Frame

Collaborative with user. Identify:
- 3–7 architectural uncertainties ranked by risk
- MVA scope (buildable in hours–days, not weeks)
- Explicit simplifications (what the MVA intentionally skips)
- Minimum viable stress criteria (what must the MVA survive to prove useful)
- Module boundaries at a level allowing independent evolution

**Exit signal:** User explicitly confirms scope is sufficient. Not "looks good" — active confirmation.

### Iterate

The generative loop. For each cycle:
1. Build or modify the scaffold to stress an uncertainty
2. Run it under the defined stress conditions
3. Record in the journal: what was tried, what happened, what was learned, what changed
4. Extract any reusable heuristic (truth that transcends this problem)

**Exit signal:** All identified uncertainties have evidence-based answers. New iterations produce diminishing returns.

### Formalize

Decompose the completed journal into spec-based output:

| Output | Source | Purpose |
|--------|--------|---------|
| `spec.md` | Journal cycles → requirements | What the system must do |
| `design.md` | Journal cycles → architecture | How the system is built |
| `lat.md` | Journal cycles → structural relationships | Architecture trace and decision graph |
| `tools.md` | Journal cycles → dependencies | Tool and dependency contract |
| `goal.md` | Spec + design + lat synthesis | Executable contract |
| `agents.md` | Execution patterns from journal | Agent behavioral instructions |

Every claim in output documents must trace to a journal cycle. Ungrounded claims get `[UNVERIFIED]` markers.

### Delete

Remove the MVA journal and scaffold code. The spec-based output is the durable artifact. The MVA was always sacrificial.

## Output Structure

When the skill completes, the target project contains:

```
project/
  spec.md       — Source of truth specification
  goal.md       — Executable contract (drives implementation)
  design.md     — System design (component architecture)
  lat.md        — Architecture trace and knowledge graph
  tools.md      — Tool and dependency contract
  agents.md     — Agent instructions for execution
  mva.md        — DELETED (sacrificial)
```

This is the standard spec-based repo pattern. Agents executing `goal.md` reference `spec.md` for constraints, `design.md` for architecture, `lat.md` for structural relationships and decisions, `tools.md` for dependencies, and `agents.md` for behavioral rules.

## When to Use

**Use when:**
- Genuine architectural uncertainty exists (can't predict right boundaries)
- Multiple plausible architectures and no evidence to choose
- Integration surface is complex or unfamiliar
- Upfront specs would be immediately obsolete
- Cost of throwaway build < cost of guessing wrong at scale

**Don't use when:**
- Architecture is obvious (standard CRUD, well-known patterns)
- Problem is algorithmic, not architectural
- No budget for building twice (MVA + real build)

## Anti-Patterns

| Anti-Pattern | Why It Fails |
|-------------|--------------|
| Premature formalization | SPEC/DESIGN before journal complete = speculation disguised as evidence |
| Scaffold attachment | Treating MVA as production code. Resisting deletion. Refactoring instead of rebuilding |
| Journal neglect | Building without recording. Formalization then relies on memory |
| Scope inflation | MVA grows to full product. Takes weeks. "Minimum" abandoned |
| Cargo-cult phases | Following steps as checklist without understanding transitions |

## Integration

- **TDD**: Use during scaffold build. Tests become journal evidence.
- **Code review**: Relaxed during MVA (code is disposable). Restored during goal execution.
- **Existing specs**: If `spec.md` already exists, MVA augments/validates it rather than replacing.
- **hermes /goal**: The `goal.md` output is directly compatible with goal-driven execution patterns.

## Files in This Skill

| File | Role |
|------|------|
| [[SKILL.md]] | This file. Entry point and overview. |
| [[spec.md]] | Methodology specification (the rules). |
| [[agents.md]] | Agent behavioral contract during MVA execution. |
| [[templates/mva.md]] | Living journal template (iteration instrument). |
| [[templates/spec.md]] | Output spec template for target projects. |
| [[templates/goal.md]] | Output goal template for target projects. |
| [[templates/design.md]] | Output design template for target projects. |
| [[templates/lat.md]] | Architecture trace and knowledge graph template. |
| [[templates/tools.md]] | Tool and dependency contract template. |
