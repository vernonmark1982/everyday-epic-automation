# Outlier-to-Clone Pipeline

Find videos massively outperforming their own channel's baseline, then reproduce
the *format* (not the content) faster than the algorithm saturates it. Most
creators check trends manually once a week; running this daily across many
niches is the actual edge.

## Why this works

`vidiq_outliers` returns a `breakoutScore`: how many multiples of a channel's
normal performance a video is currently doing. A small channel suddenly doing
50-100x its average is a strong signal the *format* (not the channel) is
working — and formats are reproducible.

## Pipeline steps

1. **Scan** — `vidiq_outliers` (YouTube) and `vidiq_ig_outlier_reels_search`
   (Instagram) for the target niche, filtered to `short` content and
   `publishedWithin: thisMonth` so the format is still fresh.
2. **Triage** — rank by `breakoutScore` first, `vph` second. Prefer short
   `videoDuration` (cheap to produce, fast to test) and low `subscriberCount`
   (proves it's the format working, not channel authority).
3. **Deconstruct** — pull the hook, pacing, and payoff from the winning video.
   Do not copy the footage/audio — copy the structural beats.
4. **Regenerate** — `vidiq_generate_video` / `vidiq_generate_broll` +
   `vidiq_voiceover_clone` or `vidiq_voiceover_generate` to produce an
   original version in the target channel's voice.
5. **Pre-flight score** — `vidiq_score_title` / `vidiq_score_thumbnail` before
   publishing; iterate with `vidiq_refine_thumbnail` if score is weak.
6. **Publish + log** — record the source outlier, the clone, and outcome in
   `pipeline/outlier-to-clone/reports/` so win-rate per niche is trackable
   over time.

## Running a scan

There's no standalone script here — the vidIQ tools are only reachable
through the MCP connection in a Claude session, so a scan is run by asking
Claude (in this repo's session) to execute step 1-2 for a given niche and
write the result into `reports/YYYY-MM-DD-<niche-slug>.md` using the template
below.

## Report template

```
# <niche> — <date>

## Top outlier
- Title / URL
- Channel size vs breakoutScore (the bigger the gap, the stronger the signal)
- Duration, VPH, view count
- Why it likely worked (1-2 sentences)

## Clone plan
- Hook (first 2-3s)
- Structure
- What to change vs the original (must be original, not a re-upload)

## Runner-up outliers
- ...
```
