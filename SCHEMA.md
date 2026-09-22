# SCHEMA.md

**Not in the original kit — recommended addition.** Every SOP says an agent "sends output to Agent X," but never defines *what that output actually looks like as data*. That's fine for manual copy-paste use; it breaks the moment you try to automate this (n8n, LangGraph, a custom orchestrator) — there's nothing for the next node to parse. This schema is the fix. Cost: one more file to keep in sync when an agent's output format changes.

## Core object: `AgentRun`

Every agent invocation produces one of these. It's a superset of the chat "Handoff Format" in `AGENTS.md` §6 — same four fields, plus what's needed to route and log programmatically.

```json
{
  "run_id": "uuid",
  "agent_id": "08",
  "video_id": "string | null",
  "channel_context": {
    "niche": "string",
    "target_audience": "string",
    "subscribers": "number",
    "avg_views": "number"
  },
  "inputs": [
    { "from_agent_id": "07", "run_id": "uuid", "field": "hook_script" }
  ],
  "deliverable": {
    "type": "string",
    "format": "markdown | json | csv | text",
    "content": "string"
  },
  "flags": [
    { "severity": "info | warning | blocker", "message": "string", "for_agent_id": "string | null" }
  ],
  "next": {
    "agent_ids": ["09", "10", "11", "14", "16", "18", "19", "21"],
    "parallel": true
  },
  "status": "complete | needs_input | blocked",
  "missing_inputs": ["string"],
  "timestamp": "ISO 8601"
}
```

## Field notes

- `agent_id` — always the two-digit string from the roster (`"01"`–`"30"`), never a name. Names change; numbers don't.
- `inputs` — array, not a single object: several agents (e.g. 08, 17) have multiple upstream sources. Reference by `run_id`, not by re-pasting content, so a pipeline can replay from any point.
- `deliverable.type` — free text matching the "Primary Output" column in the roster (e.g. `"full_video_script"`, `"thumbnail_brief"`) — pick one canonical string per agent and keep it stable; it's how downstream nodes know what they received.
- `next.parallel` — `true` when `next.agent_ids` has no dependency on each other (see the parallel branches in `WORKFLOW.md`'s Pipeline 1). An orchestrator can fan these out concurrently instead of serially.
- `status: "needs_input"` — use this instead of guessing. Pairs with `missing_inputs` (plain-language list) so a human or upstream agent knows exactly what to supply. This is the schema-level version of the Context Gate in `AGENTS.md` §4 — don't let an automated run silently fabricate a missing input.
- `flags` — carries forward the "Flags & Recommendations" concept from each SOP's Phase 3, but structured so a routing layer can act on `severity: "blocker"` (halt the pipeline) vs `"info"` (log and continue).

## What this enables

- Replaying or re-running a single agent without re-running the whole pipeline (fetch its `inputs` by `run_id`).
- Fanning out the parallel branches in `WORKFLOW.md` (09–16 after 08; 18–21 after 17) instead of running them serially, which is the actual time-cost bottleneck in the manual version of this system.
- A real audit trail: every deliverable is traceable to the exact upstream runs that produced it.

## What this doesn't cover

External-facing outputs (25's outreach emails, 27's sponsor pitches, 19's cross-platform posts) don't have a `next` agent — `next.agent_ids` is an empty array and `status` is terminal. Don't force these into a fake handoff just for schema consistency.
