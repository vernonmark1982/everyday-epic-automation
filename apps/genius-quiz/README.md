# The Genius Test

Single-file, no-build HTML app: a 10-question IQ/trivia quiz with a
shareable "genius rank" result. Built for virality (share button copies a
brag-worthy result + link) and ad/upsell monetization.

## Run locally

```
cd apps/genius-quiz
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy

It's a static file — drop `index.html` on GitHub Pages, Netlify, Vercel,
or Cloudflare Pages with zero config.

## Monetization hooks (marked `TODO(monetization)` in the code)

- Two ad-slot `<div>`s (top/bottom banner) — drop in an AdSense/Ezoic/
  Monumetric snippet once an account exists.
- A "Get My Certificate — $2.99" upsell button — point `#certificate-link`
  at a real Gumroad/Stripe Payment Link/Lemon Squeezy checkout URL.

## Extending

- Add more questions to `QUESTION_BANK` in `index.html` to avoid repeats
  for returning visitors.
- Swap the question set for a niche-specific genius test (e.g. "Movie
  Genius Test", "Money Genius Test") to target different ad/affiliate
  verticals — same engine, new content.
