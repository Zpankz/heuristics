# LAT

**Living Architecture Trace**

---

## Purpose

`LAT.md` is the **meta-document** of the Heuristics methodology.

While individual Heuristics runs produce governance layers for specific systems, the Living Architecture Trace records how the *practice of discovering architecture* itself evolves over time.

It captures:
- Heuristics and patterns that have generalized across multiple projects.
- Recurring failure modes in MVA scoping or H2 execution.
- Evolution of the governance layer schema and artifact formats.
- Refinements to the phase gates that were forced by real usage.
- Meta-heuristics about the planning process (how humans and agents most effectively perform empirical architectural discovery).

It is the closest thing this methodology has to a "cumulative wisdom" document.

---

## Entry Format

Each major entry should follow this structure:

```markdown
## [Date] — [Project / Domain] — [Short Descriptive Title]

**Context:** One-sentence description of the system being planned.

**Key Discoveries / Refined Heuristics:**
- ...

**Governance Schema Evolution:**
- New section or field added to the governance layer template, or
- Existing section that proved insufficient, with how it was strengthened.

**Phase Gate / Process Refinement:**
- What in H0–H5 was too loose, too strict, or missing, and what change was made (or should be made to SPEC.md).

**Meta-Heuristic (if any):**
- A higher-order observation about how to *do* Heuristics well.

**Evidence:** Link to the specific governance layer, iteration log, or post-mortem from that run.

**Impact on Future Runs:**
- How this changes scoping, stress criteria, or synthesis approach going forward.
```

---

## Initial Seed Entries (May 2026)

### 2026-05-16 — Creation of the Methodology Itself — "The Cost of Weak Minimum Viable Stress"

**Context:** The initial definition of the Heuristics methodology (H0–H5, SPEC.md, templates, dual Claude/Grok skills).

**Key Discoveries / Refined Heuristics:**
- The single most important quality gate is the H2 → H3 transition ("Minimum Viable Stress").
- Without at least one real distributed failure + one evolved cross-cutting concern, the resulting governance layer is dangerously convincing but structurally weak.
- "We did a lot of iteration" is not evidence. "We changed our mind about the saga boundary after seeing compensation explode under injected latency" is evidence.

**Governance Schema Evolution:**
- Added explicit "Day One Regret" retrospective in the Observability section of the governance layer template. This forces the synthesis step to surface observability debt that was only visible in hindsight during H2.

**Phase Gate / Process Refinement:**
- The original draft of H2 did not have a formal "Minimum Viable Stress" checklist. After reflection during the creation of the skill, it was elevated to a blocking gate with specific, auditable criteria.
- The explicit `mva/DEPRECATED.md` ritual in H4 was added after realizing that psychological attachment to the MVA is the most common way this methodology fails in practice.

**Meta-Heuristic:**
- "The quality of a governance layer is inversely correlated with how much the creators still like their MVA."

**Evidence:** The design discussions and template evolution that occurred while building `SKILL.md`, `SPEC.md`, `templates/governance-layer.md`, and `references/phase-gates.md`.

**Impact on Future Runs:**
- Future H2 phases will be explicitly measured against the Minimum Viable Stress checklist before the user is allowed to request H3 synthesis.
- The skill will be more aggressive about suggesting failure injection scenarios when the iteration log shows only happy-path evolution.

---

### 2026-05-16 — Dual-Harness Implementation — "Shared Spec + Divergent Adapters"

**Context:** Decision to maintain both a full Claude Code skill and a packed Grok skill that share the same methodology.

**Key Discoveries:**
- Trying to write a single "universal" skill prompt that works equally well in both harnesses produces weak integration in both.
- The methodology (H0–H5, gates, artifact contracts) can and should be harness-agnostic.
- The adapters (how you do failure injection, how you maintain iteration context, what sub-agents or tools you call) are highly harness-specific.

**Governance Schema Evolution:** N/A (this was a meta-decision about the skill, not a system being planned with Heuristics).

**Phase Gate / Process Refinement:**
- Added the principle that any harness-specific automation must still enforce the core gates (especially Minimum Viable Stress and the H4 deprecation ritual).

**Meta-Heuristic:**
- "The more powerful the harness, the more dangerous it is to let it paper over a weak H2."

**Evidence:** The creation of both `SKILL.md` (Claude) and `.grok/skills/heuristics/SKILL.md` (Grok) from the same `SPEC.md`.

**Impact on Future Runs:**
- When new harnesses are added (e.g., a web-based Heuristics runner, or a batch mode for multiple small MVAs), they must be evaluated against whether they strengthen or weaken the user's ability to feel the real stress of the MVA.

---

## Usage Guidelines

- Do not add an entry for every Heuristics run. Only add entries when something material changed in how the methodology should be practiced.
- LAT entries are higher signal than individual project governance layers for the long-term evolution of the discipline.
- The LAT should be one of the first documents read by anyone who wants to deeply understand or contribute to Heuristics (after `GOAL.md` and `SPEC.md`).

---

**Status:** Seed version (May 2026) — two initial meta-entries from the creation of the methodology itself. Future entries will come from real usage on external projects.