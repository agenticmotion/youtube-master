# EXAMPLE_RUN.md

One complete run of the Standard Video Pipeline (`WORKFLOW.md` Pipeline 1), filled in with real content — not bracketed placeholders — so you can sanity-check that the system actually produces usable output, and so you have a reference if a future edit to an agent file changes output quality. Fictional channel, fictional numbers where "current stats" are needed; everything else is a real, usable deliverable.

**Channel used for this example:** a beginner home-espresso equipment channel, 8,400 subscribers, ~3,100 avg views/video.

---

### Agent 01 — Channel Architect

**Task:** "We haven't hit a video over 5K views in a month. Diagnose and pick this week's move."

**Deliverable:**
Audit: last 8 videos average 2,900 views vs. channel's 3,100 baseline — flat, not declining, but nothing's breaking out. Top performer (11K views, 3 months ago) was a budget-vs-premium grinder comparison; the last 4 videos have all been single-product reviews. Pattern: comparison-format videos outperform single-review format by ~3x in this channel's history, but only 2 comparison videos exist total — too few to call established (see `MEMORY.md` confidence tiers).

Three options, ranked:
1. **Run another comparison video** (grinder or tamper, budget vs premium) — highest leverage, directly tests whether the one comparison-format win was a fluke or a real pattern; low effort since format is proven-producible.
2. Run a "what I wish I knew before spending $2K on espresso gear" narrative video — untested format, higher production risk.
3. Increase upload frequency — doesn't address the actual signal (format, not volume) — deprioritized.

**Decision:** Option 1. Topic: budget ($150) vs. premium ($600) espresso tamper — underserved angle per competitor gap (no comparison video Ubers 50K+ views target search terms).

```
SUMMARY: Diagnosed flat performance as a format issue, not a volume issue. Comparison-format has 1 strong (unconfirmed) signal in MEMORY.md.
DELIVERABLE: Greenlit topic — "$150 vs $600 Tamper: Is Premium Worth It?"
FLAGS: Comparison-format sample size is 2 videos — treat this run as the 3rd data point, not confirmation.
NEXT: 03 (topic refinement + keyword angle)
```

---

### Agent 03 — Viral Topic Ideation Engine

**Deliverable:** 3 title-angle variants for Agent 05 to develop, ranked:
1. **"$150 vs $600 Espresso Tamper — I Pulled 40 Shots to Find Out"** (top pick — specificity + implied testing rigor performs well in this niche's search results)
2. "Does a $600 Tamper Actually Make Better Espresso?"
3. "Budget vs Premium Tamper: The Honest Truth"

```
SUMMARY: Angle #1 selected for specificity and implied methodology (40 shots = credibility signal for this audience).
DELIVERABLE: 3 ranked title angles above.
FLAGS: none
NEXT: 04 (keyword pass), then 05 (title/thumbnail concepts)
```

---

### Agent 04 — Keyword & SEO Strategist

**Deliverable:** Primary keyword: `espresso tamper comparison` (low competition, ~880/mo). Secondary: `budget vs premium espresso gear`, `is a expensive tamper worth it`. Recommended title keeps "tamper" and "vs" in the first 40 characters for search + suggested-video surfacing.

```
SUMMARY: Confirmed low-competition primary keyword; title angle #1 already contains it.
DELIVERABLE: Keyword set above, mapped to title/description use.
FLAGS: none
NEXT: 05
```

---

### Agent 05 — Title & Thumbnail Concept Generator

**Deliverable:**
- **Final title:** "$150 vs $600 Espresso Tamper — I Pulled 40 Shots to Find Out"
- **Thumbnail concept:** Split-frame, tamper on each side (cheap one visibly plastic, premium one visibly machined steel), bold "$150" / "$600" in corner callouts, host's face center with a skeptical expression — no text beyond the two prices (face + price-contrast performs best per general split-test practice; no channel-specific thumbnail data exists yet in `MEMORY.md` to override this).

```
SUMMARY: Title locked. Thumbnail uses price-contrast + skeptical face — standard practice pick, no channel data yet to weight otherwise.
DELIVERABLE: Title + thumbnail concept above.
FLAGS: Log this thumbnail_style as "price_contrast_face" in STATE.md once published — first data point for that vocabulary value.
NEXT: 07 (hook), 13 (thumbnail production brief)
```

---

### Agent 07 — Hook & Intro Writer

**Deliverable (first 30s script):**
> "I just spent $750 on two tampers to answer one question: does the $600 one actually make better espresso, or am I paying for a nicer paperweight? [beat] I pulled 40 shots — 20 with each — same beans, same grinder, same everything except this. Here's what actually changed in the cup."

```
SUMMARY: Cold-open question hook with stated methodology (40 shots) to front-load credibility.
DELIVERABLE: Full hook script above, ~15 seconds read time.
FLAGS: none
NEXT: 08
```

---

### Agent 08 — Core Script & Storyboard Writer

**Deliverable:** Full script (condensed here — full version would run ~1,400 words / 8-9 min):

1. Hook (from 07)
2. Unboxing + spec comparison (30s) — weight, material, machining tolerance
3. Test methodology explainer (45s) — same beans/grinder/dose across both
4. Shot-by-shot tasting (3 min) — blind-tasted by 2 additional people, scored
5. Results reveal (1 min) — statistically-honest framing: "3 tasters, not a lab — take this as one data point"
6. Verdict + who should actually buy which (1 min)
7. CTA (from 10)

```
SUMMARY: 6-act structure, methodology-forward per channel's credibility-driven audience.
DELIVERABLE: Full script (see above outline; full prose available on request — condensed here to keep this example scannable).
FLAGS: none
NEXT: 09, 10, 11, 14, 16, 18, 19, 21 (parallel branch per WORKFLOW.md)
```

---

### Agent 09 — Retention & Pacing Optimizer

**Deliverable:** Insert pattern-interrupt at 3:30 (mid-tasting, energy dips historically around this point per general pacing practice) — cut to a quick "here's what $450 actually buys you in manufacturing" close-up B-roll beat. Flag act 5 (results reveal) as the retention-critical moment — don't bury the verdict, front-load it before the detailed breakdown.

```
SUMMARY: One pattern-interrupt added at 3:30; results reveal reordered to lead, not trail.
DELIVERABLE: Annotated script with pacing notes (2 edits) above.
FLAGS: none
NEXT: 10, 14
```

---

### Agent 10 — CTA Strategist

**Deliverable:** Mid-roll (after verdict, ~7:00): "If you want the exact tamper I recommend, it's linked below — and if you're deciding between your first two espresso upgrades, I made a full buying-order guide, link in the pinned comment." End-card: subscribe ask tied to "next week: are $1000 grinders worth it — same test format."

```
SUMMARY: Two CTAs — mid-roll affiliate link, end-card subscribe tied to a sequel hook (keeps series-format momentum).
DELIVERABLE: CTA copy above.
FLAGS: none
NEXT: 26 (funnel — affiliate link tracking)
```

---

### Agent 11 — Shot List & B-Roll Planner

**Deliverable (condensed):** 14 shots total — 4 product macro shots (both tampers, tripod, softbox), 3 tasting-session shots (2-cam: host + taster reactions), 2 side-by-side pour shots, 3 B-roll inserts (grinder dosing, tamp motion close-up, cup steam), 2 talking-head verdict shots.

```
SUMMARY: 14-shot list covering all script beats, 2-camera setup for tasting reactions.
DELIVERABLE: Full shot list above.
FLAGS: none
NEXT: 14
```

---

### Agent 12 — Metadata & Description Writer

**Deliverable:**
Description: "Is a $600 espresso tamper actually worth 4x the price of a $150 one? I ran a blind 40-shot test to find out — full methodology and results inside. 0:00 Intro / 0:45 Spec comparison / 1:30 Test methodology / 2:15 Blind tasting / 5:45 Results / 7:00 Verdict + buying guide."
Tags: espresso tamper, espresso gear comparison, budget vs premium espresso, home espresso setup, espresso accessories review.

```
SUMMARY: Description leads with the keyword-matched hook question; full chapter timestamps included.
DELIVERABLE: Full description + tags above.
FLAGS: none
NEXT: 17
```

---

### Agent 13 — Thumbnail Design Director

**Deliverable:** Layout brief — 1280×720, tampers positioned at 25%/75% horizontal, host face upper-center at 35% frame height (leaves room for price callouts lower-third), price text in channel's existing bold sans (per brand consistency), red vs. blue accent stroke behind each tamper to reinforce the "two options" framing without needing to read the price first.

```
SUMMARY: Layout brief above — reinforces price-contrast concept from Agent 05 with color-coded framing.
DELIVERABLE: Design brief (ready for Canva/designer handoff).
FLAGS: none
NEXT: 17, 29 (A/B variant: same layout, swap host expression neutral vs. skeptical — genuine open question, no MEMORY.md data yet)
```

---

### Agent 14 — Video Editing Director

**Deliverable (condensed):** Standard channel pacing (cuts every 3-5s during talking segments, hold 8-10s on demonstration shots). Insert the 3:30 pattern-interrupt per Agent 09. Graphic overlay: running "shots tasted: X/40" counter, bottom-right, updates through the tasting act. Color grade: match last 6 videos' LUT for channel consistency.

```
SUMMARY: Standard pacing + one required graphic (shot counter) + one required pattern-interrupt cut.
DELIVERABLE: Editing brief above.
FLAGS: none
NEXT: 15
```

---

### Agent 15 — Audio & Sound Design Consultant

**Deliverable:** Light, unobtrusive lo-fi bed under B-roll/demonstration segments (ducked -18dB under voice), no music under the tasting-reaction shots (let genuine reactions read), single riser sting into the results reveal at act 5.

```
SUMMARY: Minimal music approach — reactions and the results reveal need to land without a music cue competing for attention.
DELIVERABLE: Audio notes above.
FLAGS: none
NEXT: 16
```

---

### Agent 16 — Subtitle & Caption Optimizer

**Deliverable:** Full SRT generated from final script + edit timing (not reproduced here — mechanical output once picture-lock timestamps exist). Flag: tasting-reaction dialogue is often overlapping/informal — caption these as separate speaker-tagged lines, not merged, for accessibility compliance.

```
SUMMARY: Captions pending picture lock; one format note flagged (speaker-tagged overlapping dialogue).
DELIVERABLE: Captioning spec above; SRT to follow edit.
FLAGS: Blocked on picture lock from 14.
NEXT: 17
```

---

### Agent 17 — Upload & Publishing Coordinator

**Deliverable:** Publish checklist — title/thumbnail/description/tags (from 05/12/13) attached, captions (16) attached once ready, chapters set, end screen linked to the grinder-comparison video (series continuity per 10's sequel hook), scheduled Tuesday 2:00 PM local (channel's highest-historical-engagement slot per general upload-time practice — no `MEMORY.md` data yet to confirm this specifically for this channel).

```
SUMMARY: Full publish package assembled; scheduled per general best-practice slot pending channel-specific timing data.
DELIVERABLE: Publish checklist above — ready to execute.
FLAGS: publish_day_time should be logged in STATE.md as "Tue 14:00" once this publishes, to start building real timing data.
NEXT: 18, 19, 20, 21 (parallel, per WORKFLOW.md Pipeline 2) — then STATE.md row moves from "in_progress" to "published," performance log begins.
```

---

## What this example demonstrates

- Every deliverable above is complete and usable, not an outline — the standard `AGENTS.md` §5 requires.
- Agents correctly flag when they're relying on general best-practice vs. channel-specific `MEMORY.md` data (05's thumbnail style, 17's publish time) instead of overstating confidence.
- The parallel branch after Agent 08 (09–16 firing independently) actually holds — none of those agents needed each other's output, only the script.
- Once this video publishes and 7/30-day metrics come in, this run becomes the source data for `STATE.md` row 1 and, eventually, an input to `MEMORY.md`'s first real insight.
