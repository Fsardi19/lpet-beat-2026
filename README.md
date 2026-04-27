# BEAT Series 2026 — Landing Page

> *Behind every routine, a shared heartbeat.*

Landing page for the BEAT Series 2026 contest — La Palma & El Tucán's program for competition baristas and brewers.

## What is BEAT

For Edition III (2026), LP&ET awards **20 boxes × 6 kg** of green, single-origin specialty coffee to 20 selected barista and brewer competitors worldwide. Selection happens through a public video contest with a transparent jury rubric (30/30/20/20) plus a community voting bonus.

## Live preview

The single-file HTML preview lives in [`preview/index.html`](preview/index.html). Open it directly in any modern browser — no build step required.

```bash
open preview/index.html
```

## Tech stack (planned for v1)

| Layer | Choice |
|-------|--------|
| Framework | React 19 + Vite + TypeScript |
| Styling | CSS modules + utility classes (matches `lpet-roasted-series-usa` convention) |
| Icons | Lucide React |
| Form backend | N8N webhook → HubSpot custom object `beat_submissions` |
| Hosting | GitHub Pages |
| Image CDN | Cloudinary `dsylu9a7k`, folder `lpet-beat/` |

## Sections

The landing is structured in 9 sections (see preview):

1. Hero — heartbeat ECG waveform on black + tagline + CTA
2. Why BEAT exists — context on the rising cost of competing
3. World Stage — WBC backdrop interlude
4. The Origin — finca panoramic interlude
5. How it works — 4-step contest mechanic
6. The rubric — transparent 30/30/20/20 + Parker-pattern aside
7. Wall of Fame — chronological timeline of past LP&ET champions (2016 → 2025)
8. Founder letter — Felipe + Jooyeon Jeon (2019 WBC Champion)
9. Final CTA + Footer

## Wall of Fame champions featured

Champions across 8 years and 6 continents — see the full timeline in `preview/index.html`. Source of truth: the official LP&ET Wall of Fame print design (2025 edition).

## Strategic brief

The full strategic brief (audience, conversion priorities, design principles, open decisions, build sequence) is maintained as the canonical source of truth in the private LP&ET centro-control repo:

```
referencias/proyectos/landing-beat-2026/BRIEF.md
```

(Access restricted — contact Felipe Sardi for visibility.)

## Build sequence

1. ✅ Brief
2. ✅ Single-file HTML preview
3. ⏳ Felipe answers 10 open decisions (deadline, hashtag, voting mechanic, etc.)
4. ⏳ Image edits → Cloudinary upload to `lpet-beat/`
5. ⏳ React + Vite migration
6. ⏳ N8N + HubSpot form backend
7. ⏳ GA4 + Meta Pixel tracking
8. ⏳ Mobile QA + LCP audit
9. ⏳ Deploy to GitHub Pages
10. ⏳ Soft launch with 2-3 known competitors → public launch

## License

Copyright © 2026 La Palma & El Tucán / Hacienda Santa Elisa SAS.
All rights reserved. Trademarks belong to their respective owners.

The Wall of Fame photo archive includes social media reposts from third parties (Onyx Coffee Lab, SCA Canada, Sprudge Media, Collaborative Coffee Source, etc.). All credits acknowledged in the live page captions.
