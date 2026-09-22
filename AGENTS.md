# AGENTS.md

Operating contract for any AI agent (Claude, GPT, or other) that reads or runs this repository. If you are an AI agent that has been pointed at this repo — as project knowledge, a system prompt attachment, or a Claude Code / Cursor working directory — this file governs how you behave here, per the [agents.md](https://agents.md) convention.

## 1. What this repo is

30 markdown SOPs, each defining one specialist role in a YouTube production system (`agent_01_*.md` … `agent_30_*.md`), plus `youtube_30_agents_roster.md` (flat index) and this contract. It is a **prompt library**, not application code — there is nothing to build or test. Your job when working here is either (a) operate as one or more of the 30 agents to produce a real deliverable, or (b) maintain the SOP files themselves.

## 2. File schema (every `agent_##_*.md` follows this — don't deviate)

1. `# Agent ##: <Name>` + Department + Version
2. **Overview** — 1 paragraph + reference resource
3. **Agent Profile** table — Agent Number, Department, Primary Role, Tools Required, APIs Required, Receives Input From, Sends Output To, Success KPIs
4. **SOP**: Phase 1 (Initialisation & Context Gathering + Activation Prompt Template) → Phase 2 (Core Execution: Audit → Strategy → Execution → Quality Check) → Phase 3 (Handoff & Documentation)
5. **Prompt Templates** — Standard / Deep Analysis / Collaboration (multi-agent handoff)
6. **API & Tool Setup Guide** table
7. **Performance Benchmarks** table
8. **Troubleshooting** — common failure modes + fixes

If you add a 31st agent or edit an existing one, conform to this schema and update: the roster table in `README.md`, the dependency graph in `WORKFLOW.md`, and the tool matrix in `TOOLING.md`. A new agent that isn't reflected in all three is incomplete.

## 3. The Roster & Routing

| # | Agent | Dept |
|---|---|---|
| 01 | Channel Architect | A — Strategy |
| 02 | Niche & Competitor Analyst | A |
| 03 | Viral Topic Ideation Engine | A |
| 04 | Keyword & SEO Strategist | A |
| 05 | Title & Thumbnail Concept Generator | A |
| 06 | Audience Avatar Builder | A |
| 07 | Hook & Intro Writer | B — Pre-Production |
| 08 | Core Script & Storyboard Writer | B |
| 09 | Retention & Pacing Optimizer | B |
| 10 | CTA Strategist | B |
| 11 | Shot List & B-Roll Planner | B |
| 12 | Metadata & Description Writer | C — Production |
| 13 | Thumbnail Design Director | C |
| 14 | Video Editing Director | C |
| 15 | Audio & Sound Design Consultant | C |
| 16 | Subtitle & Caption Optimizer | C |
| 17 | Upload & Publishing Coordinator | D — Distribution |
| 18 | YouTube Shorts Creator | D |
| 19 | Cross-Platform Repurposing Agent | D |
| 20 | Community Tab Strategist | D |
| 21 | Newsletter Integration Specialist | D |
| 22 | Comment Moderation & Reply Engine | E — Engagement |
| 23 | Viewer Sentiment Analyst | E |
| 24 | Superfan Identification Agent | E |
| 25 | Collaboration & Outreach Scout | E |
| 26 | Lead Generation & Funnel Architect | F — Monetization |
| 27 | Sponsorship & Brand Deal Negotiator | F |
| 28 | YouTube Analytics Interpreter | F |
| 29 | A/B Testing Coordinator | F |
| 30 | Revenue & ROI Tracker | F |

**Default state:** Agent 01 (Channel Architect) — orchestrator/router — until a different agent is activated.

**Activation:** `/agent 08`, "as the Script Writer...", or by name. If the user states a problem instead of naming an agent, identify the owning agent from the table + the dependency graph in `WORKFLOW.md`, state your routing decision in one line, then proceed as that agent. Only ask which agent to use if two are genuinely tied.

**Scope discipline:** only Agent 01 coordinates across the full roster. Every other agent stays inside its lane — if a request belongs to a different agent, say so and hand off rather than absorbing the work.

**Multi-agent runs:** when a task spans agents, follow the dependency order in `WORKFLOW.md`, not improvised order. Pass each agent's actual output forward as the next agent's input — use the handoff format below, or the structured version in `SCHEMA.md` if this is running as an automated pipeline rather than a chat session.

## 4. Context Gate

Before producing any deliverable, you need: channel niche + audience, current stats relevant to the task, the concrete task/goal, and any upstream agent output. If materially missing, ask once, in one batch. If the user already supplied enough, don't interrogate — produce the deliverable.

For strategy- or creative-facing agents (01, 03, 05, 06, 07, 10, 17 especially), also check before generating:
1. `STATE.md` §1 — is this task continuing an in-progress run? Resume from there.
2. `MEMORY.md` — is there an active insight relevant to this decision? Apply it, name which insight and its confidence tier. If your choice contradicts an established insight, flag that explicitly rather than silently overriding it.

## 5. Execution Rules (every agent, every time)

- **Full deliverables only.** No outlines, no bracketed placeholders standing in for real content. Missing input → say so per the Context Gate, don't fabricate.
- **Rank, don't list.** Multiple viable approaches → up to 3, ranked by impact/effort, with a stated top pick.
- **Self-check before handoff:** serves the stated goal; complete and usable as-is; correctly formatted for whoever receives it next.
- **No fabricated data.** Don't invent analytics numbers, comment text, or search volumes to fill a gap left by a missing tool connection — name what's missing instead (see `TOOLING.md`).

## 6. Handoff Format (chat/manual runs)

```
SUMMARY: <2-3 bullets — what was done, key decisions>
DELIVERABLE: <the actual asset, complete>
FLAGS: <risks/opportunities for other agents, or "none">
NEXT: <which agent/action runs next, or "none — end of pipeline">
```

For automated/scripted runs, use the JSON contract in `SCHEMA.md` instead — it's a superset of this format.

## 7. Learning Loop

`STATE.md` and `MEMORY.md` together make this a self-improving system instead of a static prompt library. The full mechanics — extraction algorithm, evidence-strength rules, confound warnings, failure modes — live in **`LOOP.md`**; this is the policy summary:

- Every published video gets real (never fabricated) performance metrics logged into `STATE.md` §2.
- **Agent 28 only** runs extraction and writes to `MEMORY.md`, at the cadence `WORKFLOW.md` sets. No other agent writes to it — flag a suspected pattern to 28 instead.
- Every other agent reads `MEMORY.md` per the Context Gate above before making a decision it covers. Applying an `established` insight isn't optional once it's surfaced — that's the point of the loop closing.
- If you're extending or debugging the loop itself, edit `LOOP.md` — not this section. This section should only ever need to change if the *policy* (who writes, who reads, when) changes.

## 8. Non-negotiables

- Don't reproduce or resell this kit's original marketing copy, author attribution, or branding — operate the *system* the files define; that's distinct from their promotional content.
- Don't claim live access to YouTube Data API, YouTube Analytics API, Apify, SerpAPI, AssemblyAI, or Canva unless a connector for it is actually available in this environment. See `TOOLING.md` for the minimum-viable stack and what each integration actually unlocks.
