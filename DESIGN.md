# DESIGN

This document describes the architectural and implementation design of the **Heuristics** skill itself (the tool), not the architectures it helps discover.

It explains the major design decisions, component boundaries, dual-harmonization strategy (Claude Code + Grok), and extensibility model.

---

## 1. High-Level Design Principles

1. **Methodology First, Harness Second**
   The core H0–H5 model, phase gates, artifact formats, and governance layer schema are harness-agnostic. The `SPEC.md` is the single source of truth. Claude and Grok implementations are adapters, not independent inventions.

2. **Sacrificial MVA, Durable Governance**
   The skill must make it psychologically and technically easy to throw the MVA away. The governance layer must feel like the valuable, reusable asset.

3. **Traceability Over Polish**
   It is better to have a slightly ugly but fully traceable governance layer than a beautiful but untraceable one.

4. **Dual-Harness by Default**
   The methodology must be usable in both the user's primary Claude Code environment and the Grok TUI environment without forcing context loss. This drove the decision to maintain two skill implementations that share templates and the canonical `SPEC.md`.

---

## 2. Component Architecture

```
heuristics/ (repo root)
├── GOAL.md
├── SPEC.md
├── DESIGN.md
├── LAT.md
├── README.md
├── AGENTS.md
├── SKILL.md                 # Claude Code skill definition (primary)
├── commands/
│   └── heuristics.md        # /heuristics slash command (Claude)
├── templates/               # Authoritative artifact templates (shared)
├── references/
│   └── phase-gates.md
├── .grok/skills/heuristics/
│   └── SKILL.md             # Grok-native packed skill (project-scoped)
└── .beads/                  # Issue tracking (planning work on the skill itself)
```

### 2.1 Shared Layer (Templates + Spec)
- `templates/` and `SPEC.md` are the contract.
- Any future implementation (new harness, web UI, batch mode, etc.) must consume or faithfully replicate these.

### 2.2 Claude Code Adapter
- `SKILL.md` + `commands/heuristics.md`
- Deep integration with `bd`, `ce-plan`, `blueprint`, `thoughtbox`, Sisyphus, etc.
- Uses the full power of Claude Code's agent ecosystem (subagents, hooks, skills).

### 2.3 Grok Adapter
- Located at `.grok/skills/heuristics/SKILL.md`
- Optimized for Grok's strengths: lean-ctx (massive context compression during H1/H2), `ctx_shell` for failure injection, strong structured output and diagram generation, `best-of-n` for parallel MVA variants or governance syntheses.
- Project-scoped by default (lives inside the repo) so that when the user is working on a Heuristics-planned system, the skill is automatically available.

---

## 3. Key Design Decisions

### 3.1 Why Two Separate Skill Implementations?

- Claude Code and Grok have fundamentally different tool surfaces, context management models, and agent orchestration patterns.
- Trying to write a single "universal" skill would have produced lowest-common-denominator prompts and weak integration in both environments.
- The shared `SPEC.md` + templates guarantee that the methodology remains consistent even when the UX and automation differ.

### 3.2 Why Put the Grok Skill Inside `.grok/skills/` in the Repo?

- Project-scoped skills in Grok are automatically available when the working directory (or a parent) contains the skill definition.
- This means that when the user is actively using Heuristics to plan a new system, the Grok skill is present without manual installation.
- It also makes the repo self-contained for contributors who use Grok.

### 3.3 Artifact Strategy

- Templates are Markdown-first and human-readable by default.
- They are deliberately structured enough that future versions of the skill (or external tools) can parse them reliably (YAML frontmatter + clear section headings + consistent bullet patterns).
- No attempt was made to make them machine-only (e.g., pure JSON) because the primary consumers during H0–H3 are humans and strong models doing reasoning.

### 3.4 Governance Layer as a First-Class, Reusable Asset

- The governance layer is intentionally designed to be more valuable than any single project's code.
- Future work (not yet implemented) will likely include:
  - A way to query across multiple governance layers (cross-project heuristic search).
  - Versioning and evolution tracking of the governance schema itself (fed by `LAT.md`).

---

## 4. Integration Points (Current and Planned)

**Current:**
- `bd` (beads) — for tracking planning work on both the methodology and on individual Heuristics runs.
- `AGENTS.md` workflow.
- Shared templates between Claude and Grok implementations.

**Strongly Desired Future Integrations:**
- `thoughtbox` / graph-of-thoughts — persist major discovered heuristics as first-class observations with evidence links.
- `lean-ctx` — heavy use during H1/H2 for efficient context while iterating the MVA.
- `ce-plan` / `blueprint` — consume the H4 `rebuild-plan.md` as a high-fidelity input.
- `best-of-n` — parallel MVA implementation variants or parallel governance syntheses.

---

## 5. Extensibility Model

The methodology is designed to be extended along two axes:

1. **Domain-specific extensions** — New sections in the governance layer for regulated domains (HIPAA, financial, safety-critical), specific tech stacks (particular event buses, particular workflow engines), or specific failure classes (Byzantine, multi-region, etc.).
2. **Harness-specific automation** — New skills or sub-agents that automate parts of H1 (scaffold generation), H2 (automated failure injection harnesses), or H3 (governance layer synthesis from logs + iteration history).

Any extension must still satisfy the Minimum Viable Stress gate and the traceability requirements in `SPEC.md`.

---

## 6. Anti-Patterns in the Skill's Own Design

- Do not make the MVA experience too pleasant — the user should feel psychological pressure to finish H2 and move to the real rebuild.
- Do not let the governance layer become a dumping ground for every observation. Curation (into `heuristics-catalog.md`) is part of H3.
- Do not weaken the H4 deprecation ritual. The moment of throwing the MVA away is load-bearing for the methodology's integrity.

---

**Status:** v0.1 — Initial design document (May 2026)