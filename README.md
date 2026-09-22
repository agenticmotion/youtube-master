# YouTube Master OS

A 30-agent production system for running a YouTube channel without a full production team. Each agent is a specialist SOP (`agent_##_*.md`) covering one function — strategy, scripting, editing, distribution, engagement, or monetization — with a defined input, output, and success metric. Wired together, they form one continuous pipeline from "video idea" to "revenue tracked."

This repo is designed to be **run**, not just read — by a human operator, or by an AI orchestrator (Claude, GPT, etc.) using [`AGENTS.md`](./AGENTS.md) as its operating contract.

## Repo Map

| File | Purpose | Audience |
|---|---|---|
| `README.md` | You are here — orientation and quickstart | Everyone |
| [`AGENTS.md`](./AGENTS.md) | Operating contract for any AI agent running this system — roster, file schema, routing rules | AI agents / orchestrators |
| [`WORKFLOW.md`](./WORKFLOW.md) | The production pipeline — dependency graph, named runs, operating cadence | Human operators |
| [`SCHEMA.md`](./SCHEMA.md) | The handoff data contract between agents (what actually gets passed, not just "sends output to") | Anyone automating the pipeline (n8n, LangGraph, custom scripts) |
| [`TOOLING.md`](./TOOLING.md) | Deduplicated tool/API requirements across all 30 agents, with a minimum-viable stack | Setup / procurement |
| `youtube_30_agents_roster.md` | Original flat roster (source data — superseded for operational use by `AGENTS.md` + `WORKFLOW.md`) | Reference |
| `agent_01..30_*.md` | Individual agent SOPs — role, activation prompt, execution steps, prompt templates | Whoever operates that agent |

## Quickstart

**Running one agent manually (copy-paste into Claude/ChatGPT):**
1. Open the relevant `agent_##_*.md`.
2. Use its Phase 1 "Activation Prompt Template," filled in with your channel's actual data.
3. Follow the Phase 2 execution steps; use Phase 3's handoff format if the output feeds another agent.

**Running this as an orchestrated system:**
1. Load `AGENTS.md` as the system's operating instructions (project instructions, system prompt, or agent config).
2. Attach the `agent_##_*.md` files as its knowledge base.
3. Activate agents by number/name, or state a goal and let the orchestrator route — see `AGENTS.md` §3.

**Planning a production run (a video, a monetization push, a content audit):**
See `WORKFLOW.md` for the named pipelines and which agents fire in what order.

## Conventions

- Agent numbering (01–30) is fixed and referenced by other agents' "Receives Input From" / "Sends Output To" fields — don't renumber without updating every file that references the changed number.
- Every agent file follows the same schema (Overview → Agent Profile → SOP Phases 1–3 → Prompt Templates → API/Tool Setup → Benchmarks → Troubleshooting). See `AGENTS.md` §4 if adding a new agent.
- "Full deliverable, not an outline" is the standing output rule for every agent — enforced in `AGENTS.md` §5, not repeated per file.

## Status

30/30 agent SOPs authored, v1.0. No automation layer built yet — this is currently a prompt-driven system operated manually or via an LLM orchestrator, not a scripted pipeline. See `SCHEMA.md` if building one.
