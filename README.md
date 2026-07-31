# Groundwork ⚽

A daily Wordle-style football geography game. Players drop a pin on a map to guess where a club's stadium is, and each guess is scored by distance — the closer the pin, the more points (max 100 per guess).

**Play it live:** [groundwork.football](https://groundwork.football)

## How it works

- **Three rounds per day** — easy, medium, and hard.
- **Scored by distance** — drop a pin, get up to 100 points based on how close you are to the real stadium.
- **Resets at midnight** — a fresh set of stadiums every day.
- **No sign-up required** — just open the page and play.
- **UK coverage** — stadiums across the Premier League, EFL, SPFL, and other UK leagues.

## Tech stack

- **Single self-contained `index.html`** — all dependencies inlined, no build step needed to serve.
- **[Leaflet.js](https://leafletjs.com/)** (v1.9.4) for the interactive map, with CARTO Voyager (no-labels) tiles.
- **Hosting:** [Netlify](https://www.netlify.com/) with continuous deployment from GitHub.
- **Domain:** registered via Namecheap, DNS handled by Netlify.

## Project structure

The game is developed across multiple source files and bundled into the deployable `index.html`:

| File | Purpose |
|------|---------|
| `index.html` | Page shell and layout |
| `stadiums.js` | Stadium data and coordinates |
| `county-polygons.js` | Simplified UK county boundary polygons |
| `game.js` | Game logic |

A Python build script inlines all dependencies into a single self-contained `index.html` for deployment.

## Building

Run the Python bundling script to inline all sources into `index.html`, then commit — Netlify picks up the change and redeploys automatically.

### Development checks

After any JS change:

```bash
node --check game.js   # syntax validation
```

A DOM ID cross-check script also compares `getElementById` calls in the JS against `id` attributes in the HTML to catch mismatches before they ship.

## Data sources

- **County boundaries:** `uk-ceremonial-counties` GeoJSON, simplified with Shapely (point-in-polygon validation ensures every stadium stays inside its county).
- **Stadium coordinates:** verified against the jokecamp GPS CSV and the FCHD gazetteer.

## Typography

- **Archivo Expanded** — display
- **Lora** (italic) — secondary
- **JetBrains Mono** — scores and metadata

## License

*(Add your license of choice here.)*
