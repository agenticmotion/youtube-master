# MEMORY.md

The system's learned knowledge — what's actually been shown to work for *this* channel, extracted from real numbers in `STATE.md`, not opinion or general YouTube best-practice. This is what makes the system improve over time instead of producing the same quality output on video 100 as video 1.

**Owner:** Agent 28 (Analytics Interpreter) writes and updates this file. Every other agent reads it (per Context Gate, system instruction §4) but does not edit it directly — flag a suspected pattern to Agent 28 instead of writing it in yourself. This keeps one disciplined process behind every claim in here, instead of 30 agents each asserting their own "seems like X works."

## How an insight gets written

1. Agent 28 pulls the relevant rows from `STATE.md` §2 for the attribute being tested (e.g. all rows' `hook_type` vs `avd_pct`).
2. Group by attribute value, compare outcomes.
3. Classify confidence by sample size — **this system will almost never have enough videos for real statistical significance, so don't claim it:**

| Confidence tier | Sample size | Language to use |
|---|---|---|
| `provisional` | 2–4 videos | "early signal, not yet actionable alone" |
| `emerging` | 5–9 videos | "directionally consistent across N of M videos" |
| `established` | 10+ videos, consistent direction | "reliable pattern for this channel" |

Never use "statistically significant," "proven," or a p-value — the sample sizes here don't support that language even when a pattern looks strong. "Consistent across N of M" is the honest version.

4. Write the entry below. When new data contradicts an existing entry, don't delete it — mark it `superseded`, add the new entry, and note why (more data, or a genuine shift, e.g. algorithm change, niche shift).

## Entry format

```
### [ID] <short claim>
- Attribute tested: <e.g. hook_type>
- Evidence: N videos, <date range>, <what was compared>
- Confidence: provisional | emerging | established
- Applies to: <which agents should use this — e.g. 03, 05, 07>
- Status: active | superseded by [ID]
- Logged: <date> by Agent 28
```

---

## Active Insights

*(empty — this file populates once `STATE.md` §2 has enough logged videos to compare. Do not seed this with assumptions, industry best-practice, or anything not derived from this channel's own `STATE.md` data — that defeats the point of a channel-specific learning system.)*

## Superseded Insights

*(empty)*

## Open Questions

Attributes being tracked in `STATE.md` §2 that don't have enough data yet to say anything — listed so Agent 28 knows what to check at the next extraction pass, and so other agents know what's still unproven rather than assuming silence means "no effect."

- Title pattern → CTR
- Hook type → AVD%
- Thumbnail style → CTR
- Publish day/time → views@7day
- CTA type → conversion (funnel/subscribe rate, once Dept F data exists)
