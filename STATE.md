# STATE.md

Two logs. Both are append/update-only — don't delete history, mark it superseded. All performance numbers must be real, sourced from YouTube Studio (or a connected analytics tool) and entered by the user or fetched live — never estimated or invented by an agent. See `AGENTS.md` §7 and the system instruction §8.

## 1. Active Pipeline Runs

One row per video currently in production. Remove a row once it reaches `published` and has at least one performance snapshot logged below.

| video_id | title (working) | current_stage | status | blocked_on | last_updated |
|---|---|---|---|---|---|
| _example_ | _"10 Mistakes Killing Your Retention"_ | 08 (script) | in_progress | — | 2026-09-22 |

**Status values:** `in_progress`, `needs_input` (see `missing_inputs` in `SCHEMA.md` if automated), `blocked`, `published`.

## 2. Published Video Performance Log

One row per video per measurement snapshot (log at 7-day and 30-day marks minimum — more snapshots = better signal for `MEMORY.md`). This is the raw data `MEMORY.md`'s insights are extracted from — keep it complete even for videos that flopped; negative results are signal too.

| video_id | publish_date | snapshot_day | title_pattern | hook_type | thumbnail_style | cta_type | publish_day_time | views | ctr_pct | avd_pct | revenue | notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| _example_ | 2026-08-15 | 7 | "number list" | "cold open question" | "face + red arrow" | "subscribe mid-roll" | "Tue 14:00" | — | — | — | — | fill with real data |

**Column definitions (keep these consistent across rows — this is what makes cross-video comparison in `MEMORY.md` possible):**
- `title_pattern` — pick from a short fixed vocabulary you define once and reuse (e.g. `number_list`, `question`, `how_to`, `versus`, `curiosity_gap`) — free text defeats pattern-matching.
- `hook_type`, `thumbnail_style`, `cta_type` — same rule: fixed short vocabulary, reused verbatim across rows.
- `ctr_pct`, `avd_pct` — from YouTube Studio, as percentages.
- `revenue` — total attributable (AdSense + sponsor + affiliate) for that video to date, in your currency.

## Maintenance

- The orchestrator updates §1 on every agent handoff (per system instruction §6).
- The user (or a connected analytics tool) supplies §2's numbers — an agent never fills these in from memory or estimation.
- When §2 has enough new rows since the last extraction (cadence set in `WORKFLOW.md`), Agent 28 runs pattern extraction and updates `MEMORY.md` — see `MEMORY.md` for that process.
