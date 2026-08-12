# 🔥 Hotpath

A daily.dev-style dev blog by **Ierofantis** (@ierofantis): field notes on systems,
scrapers, and the games in between. Static HTML/CSS + a tiny vanilla-JS feed. No build,
no dependencies, no framework.

## Structure

```
hotpath/
├── index.html          # homepage: hero, JS-rendered feed, sticky Projects sidebar
├── articles.json       # feed data — the source of truth for the post list
├── articles/           # one static .html per post (9 so far)
├── assets/style.css    # the whole design system
├── render.yaml         # Render static-site blueprint
└── README.md
```

## How the feed works

The homepage does not hard-code posts. It fetches `articles.json` and renders cards,
**lazy-loaded 6 at a time** via an `IntersectionObserver` (infinite scroll), so the
feed stays fast no matter how many posts exist. Each article is a plain static HTML
file that never changes as the list grows. A `<noscript>` block lists every post for
no-JS readers and crawlers.

## Run locally

The feed uses `fetch('articles.json')`, which browsers block on `file://`, so you need
a local server (opening the file directly shows an empty feed):

```bash
python -m http.server 8000    # then visit http://localhost:8000
```

## Deploy to Render

**Static Site (simplest):** dashboard → New → Static Site → connect the repo →
Build Command empty, Publish Directory `.`. Every push redeploys.
**Blueprint:** New → Blueprint uses `render.yaml` (same result).

## Adding a new post

Use the **hotpath-writer** skill (`/hotpath-writer`), or by hand:
1. Write `articles/<kebab-slug>.html` (copy any existing article as a template; keep
   the byline `@ierofantis` and footer).
2. **Prepend one entry** to `articles.json` (newest first):
   ```json
   { "slug": "kebab-slug", "cover": "cv-shield", "emoji": "🛡️", "cat": "Systems",
     "title": "...", "excerpt": "...",
     "tags": [{"label":"Primary","cls":"t-blue"},{"label":"Tag"}],
     "read": "N min read", "note": "Adapted from <i>Book</i>" }
   ```
   Cover / tag palette: `cv-fire`+`t-orange` (games), `cv-graph`+`t-green` (data),
   `cv-shield`+`t-blue` (scraping/systems), `cv-build`+`t-purple` (architecture).

No `index.html` edit needed for a post. Only the Projects sidebar (in `index.html`) is
hand-maintained.

## Attribution

- **Stack Panic** and **Grapple Dojo** are mine — [github.com/Ierofantis](https://github.com/Ierofantis).
- **GrappleMap** is by **Eelis van der Weegen** — [github.com/Eelis/GrappleMap](https://github.com/Eelis/GrappleMap) · [eel.is/GrappleMap](http://eel.is/GrappleMap/). Grapple Dojo builds on its public-domain data; the deep-dive article is not a claim of authorship.
- Systems posts are distilled from my books *The Quiet Fetch*, *Refactoring Unified*, and *Ordered by Design* ([book](https://teopanta.gumroad.com/l/ordered_by_design)).
