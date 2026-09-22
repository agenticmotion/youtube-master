# CHANGELOG.md

Tracks the orchestration layer built on top of the original 30 SOP files (`agent_01..30_*.md`, `youtube_30_agents_roster.md`) — those stay at their original v1.0 and are logged here only when actually edited. This file is what makes future changes reviewable instead of silent.

## v1.1 — 2026-09-22

**Added**
- `STATE.md` — pipeline status tracker + published-video performance log (real, measured metrics only)
- `MEMORY.md` — self-improving insight layer; Agent 28 extracts evidence-tagged patterns from `STATE.md` on a set cadence, other agents consult it via the Context Gate
- `EXAMPLE_RUN.md` — one fully worked Standard Video Pipeline run with real (non-placeholder) deliverables at every stage
- `CHANGELOG.md` — this file

**Changed**
- System instruction (`youtube-master-os-system-instruction.md`) → v1.1: removed duplicated roster/routing content (now defers to `AGENTS.md` as single source of truth), repointed multi-agent routing from the old flat roster grouping to `WORKFLOW.md`'s actual dependency graph, added `STATE.md`/`MEMORY.md` checks to the Context Gate, added a Fallback section for environments that can't attach project files

**Rationale:** the system instruction and `AGENTS.md` had drifted into two sources of truth for the same rules (roster, routing) — first divergence between them would have gone unnoticed. Fixing that, plus adding a real learning loop instead of the system repeating the same quality of output indefinitely, was the point of this version.

## v1.0 — 2026-09-20 (documentation layer)

**Added**
- `README.md`, `AGENTS.md`, `WORKFLOW.md`, `SCHEMA.md`, `TOOLING.md`
- Initial orchestrator system instruction

**Context:** original kit (30 agent SOPs + flat roster) treated as source data; this layer made it operable as one routed system rather than 30 documents copy-pasted by hand.

## How to log a future change

One entry per version bump, dated, with **Added / Changed / Removed** subheadings (omit empty ones) and a one-line rationale if the change isn't self-explanatory. Bump the minor version (v1.x) for additions/fixes to the orchestration layer; reserve a major bump (v2.0) for a change to the agent roster itself (adding/removing/renumbering an agent) since that ripples through `AGENTS.md`, `WORKFLOW.md`, `SCHEMA.md`, and every cross-referencing agent file per `AGENTS.md` §2.
