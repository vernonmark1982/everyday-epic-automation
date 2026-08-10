# Trend Autopsy

Take a video that's already winning (or unexpectedly flopping) and dissect
*why*, using the scoring tools instead of guessing. The autopsy itself is
also publishable content — "why did this blow up" shorts are a proven
sub-genre and double as free credibility marketing for the tooling.

## Pipeline steps

1. **Pick a specimen** — an outlier from `vidiq_outliers` (for a win-autopsy)
   or a known underperformer (for a flop-autopsy).
2. **Score the title** — `vidiq_score_title` (0-100, CTR potential).
3. **Score the thumbnail** — `vidiq_score_thumbnail` (0-100 + itemized
   strengths/weaknesses).
4. **Pull velocity history** — `vidiq_video_stats` to see whether growth was
   a slow build or an instant spike (changes the explanation).
5. **Synthesize** — the autopsy isn't "the title scored 91" by itself, it's
   *why* the score landed there and what that implies for what actually
   drove the result (e.g. title carrying the click vs. thumbnail carrying
   it vs. neither — algorithmic push from engagement velocity).
6. **Publish + log** in `reports/`.

## Report template

```
# <video> — <date>

## Scores
- Title score: X/100
- Thumbnail score: Y/100 (strengths / weaknesses)
- Velocity: instant spike vs slow build

## The real driver
What actually explains the performance, in plain terms.

## Takeaway for our own content
What this changes about how we title/thumbnail our own videos.
```
