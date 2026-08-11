# 🔥 Hotpath

A daily.dev-style dev blog by **Ierofantis** — field notes on systems,
scrapers, and the games in between. Pure static HTML/CSS, zero build, zero dependencies.

## Structure

```
hotpath/
├── index.html                 # the feed (card grid of all posts)
├── articles/
│   ├── scrapers-six-surfaces.html            # from The Quiet Fetch
│   ├── stack-panic-call-stack-furnace.html   # my game: github.com/Ierofantis/stack_panic
│   ├── config-over-code-human-ceiling.html   # from Refactoring Unified
│   └── grapplemap-grappling-as-a-graph.html  # deep dive, credit: Eelis/GrappleMap
├── assets/
│   └── style.css              # the whole design system
├── render.yaml                # Render static-site blueprint
└── README.md
```

## Run locally

No server needed. Open `index.html` in a browser, or:

```bash
python -m http.server 8000    # then visit http://localhost:8000
```

## Deploy to Render (static site)

**Option A — Blueprint (recommended):** push this folder to a Git repo and, in the
Render dashboard, choose **New → Blueprint**, point it at the repo. `render.yaml`
does the rest (static, no build, publish `.`).

**Option B — Manual:** Render dashboard → **New → Static Site** → connect the repo →
- **Root Directory:** `hotpath` (only if this folder is a subdirectory of the repo)
- **Build Command:** *(leave empty)*
- **Publish Directory:** `.`

That's it. Render serves the files directly; every push redeploys.

## Adding a new post

Use the **hotpath-writer** skill (`/hotpath-writer`), or by hand:
1. Copy any file in `articles/` as a template.
2. Write the post, keep the byline and footer.
3. Add a `<a class="card">…</a>` block to the grid in `index.html`.
   Cover classes: `cv-fire` (games), `cv-graph` (data/graphs), `cv-shield`
   (scraping/systems), `cv-build` (architecture).

## Attribution

- **Stack Panic** is mine — [github.com/Ierofantis/stack_panic](https://github.com/Ierofantis/stack_panic).
- **GrappleMap** is by **Eelis van der Weegen** — [github.com/Eelis/GrappleMap](https://github.com/Eelis/GrappleMap) · [eel.is/GrappleMap](http://eel.is/GrappleMap/). The article is a deep dive, not a claim of authorship.
- The systems articles are distilled from my books *The Quiet Fetch* and *Refactoring Unified*.
