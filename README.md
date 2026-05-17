# Heuristics

Collection of reasoning heuristics implemented as Claude Code skills.

## Skills

| Skill | Path | Purpose |
|-------|------|---------|
| `/mva` | `mva/` | Iterative architecture discovery through disposable builds |

## Usage

Skills are symlinked into `~/.claude/skills/` for Claude Code discovery. Invoke via `/mva` in any Claude Code session.

## Structure

Each skill is self-contained in its own directory with a `SKILL.md` entry point containing YAML frontmatter for registration.
