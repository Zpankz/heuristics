# Templates for the MVA Skill

Production-ready templates for applying the MVA methodology to a new high-uncertainty architectural problem. Copy, fill variables, follow lat.md conventions. Do not modify templates in place — copy into your target project. See [[../SKILL.md]] for invocation and [[../spec.md]] for methodology rules.

## Document Lifecycle

The lifecycle is strict. Deviating from the order corrupts the evidence trail.

1. **mva.md** — Start here. Written iteratively as a living journal during active discovery. This is the primary artifact — everything else derives from it.
2. **spec.md + design.md + lat.md + tools.md** — Created only after mva.md is considered complete and validated. Formalize the architecture by decomposing MVA learnings into specification, design, architecture trace, and tool contract.
3. **goal.md** — Synthesized from the completed mva.md + spec.md + design.md + lat.md. Becomes the executable contract handed to the implementing agent.
4. **mva.md is deleted** — Sacrificial by design. Its work is done; it has been distilled into the six output documents.
5. **agents.md created** — Agent behavioral instructions for executing the goal, produced alongside goal.md.

## How to Use These Templates

Three steps. No shortcuts.

1. Copy the relevant template into the root of your target project (or the appropriate subdirectory).
2. Replace all `{{VARIABLE_NAME}}` placeholders with concrete content as early as possible.
3. Follow lat.md conventions in the resulting file: every section begins with a leading identity paragraph (≤250 chars), use `[[wikilinks]]` for cross-document references, keep sections agent-navigable.

## Template Overview

Six templates, each with a specific role in the lifecycle.

| Template | Purpose | When to Use |
|----------|---------|-------------|
| [[mva.md]] | Living journal — what worked, what failed, evolving understanding | During active discovery, from first iteration until MVA is validated |
| [[spec.md]] | Formal, stable technical specification | After mva.md is validated and complete |
| [[design.md]] | Technical design and implementation approach | After mva.md is validated and complete |
| [[lat.md]] | Architecture trace — component graph, decisions, constraints | After mva.md is validated and complete |
| [[tools.md]] | Tool and dependency contract | After mva.md is validated and complete |
| [[goal.md]] | Executable contract synthesizing all prior work | After all other outputs exist |

## Variables

Common `{{VARIABLE_NAME}}` placeholders used across all templates.

| Variable | Used In | Meaning |
|----------|---------|---------|
| `{{PROJECT_OR_FEATURE_NAME}}` | All | Scopes the document to a specific project or feature |
| `{{DATE}}` | All | Date the document was created or last updated |
| `{{AGENT_OR_PERSON}}` | mva, goal, lat, tools | Owner responsible for this engagement |
| `{{BRIEF_DESCRIPTION_OF_THE_ARCHITECTURAL_PROBLEM}}` | mva | Starting hypothesis; will evolve during iteration |
| `{{VERSION}}` | design, spec | Semantic version of the formalized document |
| `{{N}}` | All output templates | Cycle number reference for traceability |

Fill these at copy time. Leaving placeholders in a live document causes agent confusion.

## lat.md Conventions

Every document produced from these templates must follow lat.md rules.

- Every section (`##`, `###`) begins with a leading paragraph that establishes the section's identity in ≤250 characters.
- Cross-references use `[[wikilinks]]` — never bare filenames or markdown links for internal references.
- Sections must be independently navigable: an agent jumping to any `##` heading should understand its scope without reading the parent.
- Frontmatter is present on all documents. Minimum: `lat: require-code-mention: false` unless code citations are needed.

## Best Practices

Hard-won rules from real MVA engagements.

**Journal during iteration, not after.** Post-hoc reconstruction loses the temporal sequence of discovery — which assumptions were wrong first, which corrections cascaded. That sequence is the evidence base for reliable formalization.

**Every claim traces to evidence.** All output documents derive from mva.md. Any claim that cannot be traced to a cycle in the journal is speculative and should be removed or flagged.

**Do not premature-formalize.** The signal that formalization is safe: new MVA iterations produce diminishing returns and no new uncertainties (including emergent ones) remain unresolved. Premature decomposition produces documents that look rigorous but contain speculation dressed as findings.

**mva.md deletion is intentional.** It is not archiving — it is signal that the discovery phase is complete and the execution phase begins. Keeping it signals unresolved uncertainty. Heuristics are extracted into lat.md before deletion.
