# GOAL

## North Star

**Heuristics exists to make the discovery of correct software architecture an empirical, first-principles, and repeatable discipline rather than an act of high-variance speculation.**

We believe that for systems with significant architectural uncertainty (novel orchestration, complex distributed state, cross-cutting governance, or domains without strong local precedent), the highest-leverage planning activity is not writing a document — it is building the smallest possible runnable probe, stressing it until it reveals its true shape, extracting the durable invariants and contracts from that stress, and only then building the production system from those extracted truths.

## Success in 18–36 Months

- A meaningful percentage of complex agentic, distributed, and orchestration-heavy systems in the user's (and eventually the broader ECC) ecosystem are planned using the Heuristics methodology instead of (or in addition to) traditional speculative planning.
- The governance layers produced by Heuristics runs become high-quality, reusable assets that improve the quality of subsequent systems (both within a project and across projects via the Living Architecture Trace).
- The methodology has been battle-tested on at least 8–12 real, high-stakes architectural problems, and the phase gates, artifact formats, and Minimum Viable Stress criteria have been refined from that evidence.
- Clear signals exist that Heuristics produces measurably better architectural outcomes (fewer late-stage refactors, stronger observability from day one, fewer "we wish we had known X earlier" incidents) than pure speculative planning on equivalent classes of problems.
- The skill is mature enough that both strong and default models can run high-quality Heuristics sessions with appropriate scaffolding.

## What We Will Not Optimize For

- Speed of initial planning (Heuristics is deliberately slower in the short term because it invests in discovery).
- Breadth (we optimize for depth on high-uncertainty problems; we explicitly recommend traditional planning tools for well-understood increments).
- Making the MVA "good enough to ship" (the MVA is planning debt by design).

## The Ultimate Measure

When an engineer or agent looks at a complex system that was planned with Heuristics and says:

> "This architecture feels like it was designed by someone who had already lived through its failure modes."

That is success.