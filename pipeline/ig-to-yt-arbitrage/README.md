# IG-to-YouTube Arbitrage

Most outlier-tracking only watches YouTube, so trends that are already
proven on Instagram Reels arrive on YouTube Shorts late and underserved.
This pipeline mines IG outliers first, then checks whether the *concept*
has already saturated YouTube — if not, that's the arbitrage window.

## Pipeline steps

1. **Mine IG outliers** — `vidiq_ig_outlier_reels_search` for the niche,
   ranked by multiple-of-account-median (not raw views — a 58K-follower
   account doing 70x its median is a stronger signal than a 49M-follower
   account doing 21x).
2. **Check for YouTube saturation** — run the same niche/keyword through
   `vidiq_outliers` (YouTube). If the *specific trick* shown in the IG reel
   isn't already appearing as its own outlier on YouTube, that's a gap.
3. **Rank gaps by reproducibility** — prefer single-take, low-prop-cost
   hacks over compilations or anything requiring rare tools/footage.
4. **Cross-post the concept, not the clip** — rebuild it as an original
   YouTube Short (own voice/branding), publish before the gap closes.
5. **Log** in `reports/`, including which gaps were taken and which were
   skipped (and why), so the niche's gap-to-saturation timeline becomes
   visible over time.

## Report template

```
# <niche> — <date>

## Gap candidates (IG-proven, not yet a YouTube outlier)
| Reel | Multiple vs account median | Followers | Reproducibility |

## Recommended first move
Which one to clone first and why.

## Already saturated on YouTube (skip)
...
```
