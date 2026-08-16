# NYC Noise Pulse 🌆🔊

**Turning 311 noise complaints into a real-time map of where — and when — New York gets loud.**

Built for the [NYPL "Built for NYC: AI" Hackathon](https://www.nypl.org/) at the Stavros Niarchos Foundation Library, in partnership with Major League Hacking and Google.org.

---

## What it does

NYC Noise Pulse is a live, interactive map that visualizes NYC 311 noise complaints across the five boroughs. It pulls directly from **NYC Open Data's 311 Service Requests dataset** and lets you explore the data in a few ways:

- 🗺️ **Density map** — complaints are aggregated into a grid and color-coded from yellow (fewer) to red (more)
- 🕐 **Hour-of-day slider** — see how noise patterns shift from daytime into late night
- 📅 **Weekday / weekend toggle** — compare residential weekday noise vs. weekend nightlife noise
- 📊 **Live stats panel** — total complaints, peak hour, and the top 3 loudest boroughs *and* neighborhoods

No backend, no build step — it's a single self-contained HTML file that runs entirely in the browser.

## Live demo

🔗 **[https://newyorknoiseapp.netlify.app]**

## How it's built

| Piece | Tech |
|---|---|
| Map rendering | [Leaflet.js](https://leafletjs.com/) with a custom canvas-free grid-density layer (no external heatmap plugin) |
| Data source | [NYC Open Data — 311 Service Requests](https://data.cityofnewyork.us/resource/erm2-nwe9.json) (Socrata API), filtered to noise complaints from the last 90 days |
| Neighborhood mapping | A hand-curated ZIP → neighborhood lookup table, since 311 data reports ZIP codes, not neighborhood names |
| Frontend | Vanilla HTML / CSS / JavaScript — no framework, no build tooling |
| Fonts | Space Grotesk, Inter, IBM Plex Mono (Google Fonts) |
| Fallback | If the live API is unreachable (e.g. restrictive wifi), the app generates a realistic synthetic dataset so the demo never shows a blank map |

## Running it locally

No install required — it's one file.

```bash
git clone https://github.com/<your-username>/nyc-noise-pulse.git
cd nyc-noise-pulse
open index.html   # or just double-click the file
```

Or deploy instantly with a static host:
- **Netlify Drop** — drag `index.html` onto [app.netlify.com/drop](https://app.netlify.com/drop)
- **GitHub Pages** — push to a repo, enable Pages in Settings → Pages

## Data source

[NYC Open Data — 311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9), filtered to `complaint_type LIKE 'Noise%'`, queried live via the Socrata Open Data API.

## Challenges

- **API reliability on public wifi** — solved with an automatic fallback to synthetic demo data if the live fetch fails.
- **ZIP-to-neighborhood mapping** — there's no single official NYC ZIP-to-neighborhood dataset, so the lookup table here is manually curated and covers common ZIPs, not the full ~180 in NYC.
- **Mobile usability** — controls, sliders, and the map are responsive and touch-friendly for in-person judging.

## Roadmap

- [ ] Expand ZIP-to-neighborhood coverage to all NYC ZIPs
- [ ] Add other 311 complaint types (heat, sanitation, parking) as toggleable layers
- [ ] Click a neighborhood to see its complaint trend over time
- [ ] Correlate noise density with other open datasets (nightlife permits, transit density)

## Built with AI ("vibe coding")

This project was built solo using AI-assisted development to scaffold the map logic, grid-density aggregation, and responsive layout, then iterated on manually — in the spirit of the hackathon's "vibe coding" prompt.

## License

MIT — free to use, fork, and build on.

## Author

Built solo for the NYPL Built for NYC: AI Hackathon, August 2026.
