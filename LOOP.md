# LOOP.md

The single source of truth for how the self-improving loop actually works — the algorithm, not just the policy. `AGENTS.md` §7 says *who's allowed to touch it*; `WORKFLOW.md` Pipeline 6 says *where it sits in the graph*; `MEMORY.md` is *the data store and entry format*. This file is the procedure Agent 28 follows to turn one into the other. Keep the mechanics here only — if you find yourself re-explaining the algorithm in one of those three files, delete it there and link here instead; that duplication is exactly what caused the v1.0→v1.1 system-instruction rewrite (see `CHANGELOG.md`).

## 1. Trigger

Runs at the cadence in `WORKFLOW.md`'s operating cadence table (every 5 published videos, by default). Can also be triggered manually ("run a memory extraction pass now") — the algorithm below doesn't change, only when it fires.

## 2. Extraction Algorithm

1. **Pull data.** Read all rows in `STATE.md` §2. Filter to rows added since the `Extraction Log`'s last entry in `MEMORY.md` (or all rows, on the first-ever run).
2. **Pick the attribute(s) to test.** Default to the list in `MEMORY.md`'s "Open Questions" plus any `provisional`/`emerging` entry in "Active Insights" that now has enough new data to potentially move up a tier. Don't re-test an `established` entry every pass just because a cadence hit — only re-test it if new data actually contradicts it (see §4).
3. **Group and compare.** For the attribute being tested, group videos by their tracked value (e.g. all `hook_type: cold_open_question` vs. all `hook_type: direct_statement`) and compare the outcome metric(s) that attribute plausibly affects:
   - `hook_type`, `title_pattern` → `avd_pct`, `ctr_pct`
   - `thumbnail_style` → `ctr_pct`
   - `cta_type` → funnel conversion (once Dept F data exists in `STATE.md`)
   - `publish_day_time` → `views` at the 7-day snapshot
4. **Classify evidence type before evidence strength:**
   - If Agent 29 ran a genuine A/B test on this attribute (two variants, same video, split-tested) → `evidence_type: controlled_ab_test`. This is real experimental evidence — one variable changed, everything else held constant.
   - If this is Agent 28 comparing different videos that happen to differ on this attribute → `evidence_type: passive_correlation`. This is much weaker: those videos almost certainly differ on other attributes too (different topic, different week, different thumbnail *and* title at once), so you cannot cleanly attribute the outcome to the one attribute being compared. Say so in the entry — don't imply causation a passive comparison can't support.
5. **Classify confidence by sample size** — see the table in `MEMORY.md`. Count only videos that isolate the attribute reasonably cleanly; if 8 videos differ on `hook_type` but also differ wildly on topic/format, note the confound rather than counting all 8 as clean evidence.
6. **Compare against existing `MEMORY.md` entries** for the same attribute:
   - No existing entry → write a new one.
   - Existing entry, new data agrees and sample size grew → update the same entry in place (bump N, bump confidence tier if the new count crosses a threshold). This is an update, not a new entry — don't create a duplicate ID.
   - Existing entry, new data disagrees → do not silently overwrite. Mark the old entry `superseded by [new ID]`, write the new entry, and state in the new entry why they disagree if you can tell (more data changing the picture, vs. an actual shift like an algorithm change or a niche pivot — these need different responses from the channel, so don't blur them together).
7. **Write to `MEMORY.md`** using its entry format, including `evidence_type`.
8. **Log the pass** in `MEMORY.md`'s Extraction Log table — date, videos considered, entries added/updated/superseded. A pass that considers data and concludes "nothing crossed a threshold" still gets logged with zero in the entry columns — an empty log row is a bug, not a quiet pass.
9. **Surface `established`-tier promotions.** If any entry moved to `established` this pass, flag it once for the user the next time Agent 01 runs (per `MEMORY.md` §5) — don't let a consequential strategy-level conclusion get applied system-wide with the user never having seen it stated plainly.

## 3. Evidence Hierarchy (when sources conflict)

1. `controlled_ab_test`, any confidence tier — real experimental evidence.
2. `passive_correlation` at `established` (10+ videos, consistent direction).
3. `passive_correlation` at `emerging`.
4. `passive_correlation` at `provisional` — treat as a hypothesis to test, not a rule to apply.

A `controlled_ab_test` result always outranks a `passive_correlation` result on the same attribute, even at lower confidence tier — see `MEMORY.md`'s entry-format note. If Agent 29 has never tested an attribute, passive correlation is what you have; use it, but never let its confidence tier imply it's as strong as a real test.

## 4. Known Failure Modes (check for these every pass, not just when something looks wrong)

- **Confounded comparisons.** Videos rarely differ on exactly one attribute. A "hook_type" comparison across videos that also differ in topic, length, and thumbnail is weak evidence for hook_type specifically — flag this in the entry rather than pretending the comparison was clean.
- **Survivorship bias.** `STATE.md` only logs videos that got made and published — it says nothing about ideas that never got produced. Don't extrapolate "this topic doesn't work" from an absence of data; that's a gap, not a negative result.
- **Small-group overfitting.** 3 videos landing in one bucket and 2 in another is not "established" no matter how different the averages look — the confidence tiers exist specifically to stop this. Don't round up.
- **Recency/seasonality confound.** `publish_day_time` patterns can just reflect when the channel happened to be uploading that month (holidays, algorithm changes, audience growth over time) rather than a real time-of-day effect. Note the date range in every entry so this is checkable later.
- **Simpson's-paradox-style reversal.** A pattern that holds within each topic cluster can reverse when clusters are pooled. If you have enough data to split by topic/format and the direction flips, report the split, not the pooled number.

## 5. What this loop is not

It doesn't run experiments on its own — Agent 29 designs and runs actual A/B tests as its own SOP; this loop only consumes those results alongside passive data. It doesn't make strategy decisions — it surfaces evidence to Agent 01, who (with the user) decides what to do with it. And it doesn't backfill missing `STATE.md` data — if the performance log is thin, the honest output of this loop is "not enough data yet," not a confident-sounding guess.
</>
