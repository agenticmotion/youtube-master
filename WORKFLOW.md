# WORKFLOW.md

The actual dependency graph between agents, extracted from each SOP's "Receives Input From" / "Sends Output To" fields — this is the real pipeline, not just the department grouping in the roster.

## Full Dependency Graph

```mermaid
flowchart TD
    subgraph A["Dept A — Strategy"]
        A1[01 Channel Architect]
        A2[02 Competitor Analyst]
        A3[03 Topic Ideation]
        A4[04 SEO Strategist]
        A5[05 Title/Thumbnail Concepts]
        A6[06 Audience Avatar]
    end
    subgraph B["Dept B — Pre-Production"]
        B7[07 Hook Writer]
        B8[08 Script Writer]
        B9[09 Retention Optimizer]
        B10[10 CTA Strategist]
        B11[11 Shot List Planner]
    end
    subgraph C["Dept C — Production"]
        C12[12 Metadata Writer]
        C13[13 Thumbnail Director]
        C14[14 Editing Director]
        C15[15 Audio Consultant]
        C16[16 Caption Optimizer]
    end
    subgraph D["Dept D — Distribution"]
        D17[17 Publishing Coordinator]
        D18[18 Shorts Creator]
        D19[19 Repurposing Agent]
        D20[20 Community Strategist]
        D21[21 Newsletter Specialist]
    end
    subgraph E["Dept E — Engagement"]
        E22[22 Comment Engine]
        E23[23 Sentiment Analyst]
        E24[24 Superfan ID]
        E25[25 Outreach Scout]
    end
    subgraph F["Dept F — Monetization"]
        F26[26 Funnel Architect]
        F27[27 Sponsorship Negotiator]
        F28[28 Analytics Interpreter]
        F29[29 A/B Test Coordinator]
        F30[30 Revenue Tracker]
    end

    A1 --> A2 & A3 & A4 & A5 & A6
    A2 --> A3 & A4 & A5
    A3 --> A4 & A5 & B7
    A4 --> A5 & C12 & D17
    A5 --> B7 & C13 & F29
    A6 --> B7 & B8 & B10

    B7 --> B8
    B8 --> B9 & B10 & B11 & C14 & C16 & D18 & D19 & D21
    B9 --> B10 & C14
    B10 --> F26
    B11 --> C14

    C12 --> D17
    C13 --> D17 & F29
    C14 --> C15
    C15 --> C16
    C16 --> D17

    D17 --> D18 & D19 & D20 & D21
    D18 --> D19
    D20 --> E22

    E22 --> E23 & E24
    E23 -.feedback.-> A3 & A6
    E24 --> E25
    E25 -.-> A2

    F26 --> F27
    F27 -.-> F28
    F28 --> A1 & F29 & F30
    F29 --> F28
    F30 --> A1
```

**Solid arrows** = required input. **Dotted arrows** = feedback/loop-back (informs future cycles, doesn't block the current one).

## Named Pipelines

### 1. Standard Video Pipeline (idea → published)
`01 → 03 → 04 → 05 → 07 → 08 → [09, 10, 11] → [12, 13, 14, 16] → 15 → 17`

Run this per video. Agents 09–16 can run in parallel once 08 (script) is done — they don't depend on each other, only on the script.

### 2. Post-Publish Distribution Pipeline
`17 → [18, 19, 20, 21]` (parallel — all four only need the published video + metadata from 17)

### 3. Engagement Loop (continuous, not per-video)
`20 → 22 → [23, 24] → 25` and `23 → back to 03, 06` (sentiment feeds future ideation and the audience avatar — this is how the system learns from its audience instead of guessing).

### 4. Monetization Loop (monthly/quarterly cadence, not per-video)
`10 → 26 → 27 → 28 → [29, 30] → back to 01` (revenue and analytics data feed back into channel strategy — this is the system's only path from "content" to "business decisions").

### 5. Optimization Loop (per-video, after publish)
`28 → 29 → 28` (A/B test results refine future analytics baselines) — this is the only genuine two-way loop; everything else is one-directional or feeds forward into the strategy loop.

### 6. Learning Loop (ties `STATE.md` and `MEMORY.md` into the pipeline)
`Published videos → STATE.md §2 (metrics logged) → 28 (pattern extraction) → MEMORY.md (insights written) → back into 01, 03, 05, 06, 07, 10, 17 (applied on future runs)`

This is what makes the system's output quality change over time instead of staying flat from video 1 to video 100. The graph edge is documented here; the actual extraction algorithm, evidence-strength rules, and failure modes are documented once, in `LOOP.md` — see that file, not this one, for how Agent 28 actually does the extraction.

## Suggested Operating Cadence

This isn't specified in the original SOPs — it's a recommended default; adjust to your actual publish frequency.

| Cadence | Run |
|---|---|
| Per video | Pipeline 1 → 2 |
| Daily/every 2-3 days | Pipeline 3 (comment engagement) |
| Weekly | 28 (analytics review) |
| Every 5 published videos | 28 runs `MEMORY.md` pattern extraction (Pipeline 6) — matches the `emerging` confidence threshold in `MEMORY.md`; running it more often than this just churns `provisional` entries with nothing new to say |
| Monthly | Pipeline 4 (monetization loop), 29 result review |
| Quarterly | 01 + 02 full strategy re-audit |

## Critical Path vs. Optional Branches

**Critical path** (a video cannot ship without these): 01 → 03 → 08 → 17. Everything else enriches or distributes that core, but 17 (publish) only hard-depends on 12, 13, 16 being done — 14/15 (edit/audio) happen outside this system entirely (they're briefs *for* a human editor, not automatable outputs).

**Optional branches:** 18–21 (repurposing), 20–25 (community/superfans), and all of Dept F are growth multipliers, not blockers — a channel can run Pipeline 1+2 alone and still publish.
