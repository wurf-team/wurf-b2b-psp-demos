# Wurf — B2B PSP Demo Video

An auto-playing HTML/CSS/JS animated demo showing a Wurf-powered AI chat widget integrated into a merchant payment dashboard.

## Quick Start

Open `index.html` in any modern browser, or serve it locally:

```bash
python3 -m http.server 8765
# then open http://localhost:8765
```

## What It Shows

A merchant ("Camden Coffee Co.") interacts with a Wurf chat widget while viewing their payment dashboard. Two scenarios play out automatically:

1. **Footfall Analysis** — The merchant asks about foot traffic trends and receives an animated chart with insights
2. **Location Scouting** — The merchant evaluates a new store location and gets a comparison table with a location score

The demo loops continuously (~33s per cycle).

## Dependencies (loaded via CDN)

- [GSAP 3](https://greensock.com/gsap/) — animation timeline
- [Chart.js 4](https://www.chartjs.org/) — data visualizations
- [Google Fonts](https://fonts.google.com/) — Plus Jakarta Sans + Space Grotesk
