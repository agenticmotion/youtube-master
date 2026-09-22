# TOOLING.md

**Not in the original kit — recommended addition.** Every agent file repeats its own "API & Tool Setup Guide," so the same tools (Notion, Google Sheets, OpenAI/Anthropic) are documented 20–30 times with no single source of truth. When a price or a tool gets swapped, that's up to 30 files to find and edit. This is that source of truth — the per-agent tables can shrink to a one-line link here. Cost: you now maintain the master list in one place instead of copy-pasting per agent, which is strictly less work, not more.

## APIs, by how many agents need them

| API | Required by (agent #) | Count | Free tier | Cost |
|---|---|---|---|---|
| OpenAI or Anthropic | All 30 | 30 | No | $20–100/mo |
| YouTube Data API v3 | 02, 03, 04, 12, 17, 20, 22, 23, 24, 25, 29 | 11 | Yes (quota-limited) | Free |
| YouTube Analytics API | 28, 30 | 2 | Yes | Free |
| Apify | 02 (also a listed tool for 23) | 1–2 | Limited | $49+/mo |
| SerpAPI | 04 | 1 | Limited | $50+/mo |
| Canva API | 13 | 1 | Yes | Free tier available |
| AssemblyAI | 16 | 1 | Yes (5 hrs/mo) | $0.37/hr audio |
| Google Trends API | 03 | 1 | Yes | Free |

## Software tools, by agent

| Tool | Used by (agent #) | Category |
|---|---|---|
| Google Sheets | 01, 02, 03, 04, 05, 11, 17, 22, 23, 24, 25, 26, 28, 29, 30 | Data/tracking |
| Google Docs | 07, 08, 09, 10, 12, 14, 16, 18, 19, 21, 27 | Writing |
| Notion | 01, 03, 05, 06, 07, 10, 11, 14, 15, 17, 19, 26 | Knowledge base |
| YouTube Studio | 02, 04, 12, 16, 17, 20, 22, 28, 29 | Platform-native |
| Canva | 05, 13, 27 | Design |
| TubeBuddy / vidIQ | 04, 29 | SEO/CTR tooling |
| AssemblyAI | 16 | Transcription |
| Opus Clip / CapCut | 18 | Short-form editing |
| Buffer / Hootsuite | 19 | Social scheduling |
| Mailchimp / ConvertKit | 21 | Email |
| Gmail / Hunter.io | 25 | Outreach |
| ClickFunnels / Systeme.io | 26 | Funnel building |
| LinkedIn | 27 | Sponsor prospecting |
| Looker Studio | 28 | Analytics dashboards |
| Epidemic Sound / Artlist | 15 | Licensed music |
| Midjourney / DALL-E / Adobe Express | 13 | Thumbnail generation |

## Minimum-Viable Stack (ranked, not padded)

**Tier 1 — required to run any agent at all.** Nothing else works without this.
- Claude or GPT API access (~$20–100/mo depending on volume)
- Google Sheets + Google Docs (free) — covers the tracking/writing needs of ~20 of 30 agents on its own

**Tier 2 — required once you're actually publishing, not just planning.**
- YouTube Data API v3 (free, quota-limited) — unlocks 11 agents' real data instead of manual entry
- YouTube Studio (free, native) — required for 12, 16, 17, 20, 28, 29 regardless
- AssemblyAI free tier — captions (agent 16)

**Tier 3 — only when a specific department becomes your bottleneck.** Don't provision these on day one; they're single-agent tools.
- Apify + SerpAPI — only if 02 (competitor analysis) or 04 (SEO) is your actual constraint
- Canva API — only if you're automating thumbnail generation past the brief stage (13)
- Mailchimp/ConvertKit, ClickFunnels/Systeme.io — only once Dept F (monetization) is active, not before

**Verdict:** start with Tier 1 + Tier 2 only (~$20–100/mo total). That alone runs the full "Standard Video Pipeline" in `WORKFLOW.md`. Everything in Tier 3 is a growth-stage unlock, not a launch requirement — buying it earlier just adds subscription cost against agents you're not using yet.

## Connector Note

If this system is being run through an AI orchestrator with tool/MCP access rather than manually: only claim access to an API above if a live connector for it actually exists in that environment. Per `AGENTS.md` §7, don't fabricate YouTube analytics, comment data, or search volume to compensate for a missing connection — say what's missing and what connecting it would unlock.
