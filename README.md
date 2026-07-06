# vwinterhager.github.io

Vincent Winterhager's personal site — live at **https://vwinterhager.github.io/**

A single self-contained HTML site: no build step, no JS framework, no external runtime
dependencies. Fonts, images, and PDFs are all bundled locally under `assets/`.

## Structure

- **`index.html`** — the whole site. Sections: full-height intro (name/title/links over an
  animated, cursor-reactive network canvas background), About (photo + bio, "Read more"
  toggle), Publications (Academic / Policy Papers), Teaching, Projects & Initiatives,
  Curriculum Vitae, Contact. Dark/light theme toggle (default: dark).
- **`imprint.html`** / **`privacy.html`** — legal pages, linked from the footer.
  ⚠️ **`imprint.html` currently has no postal address filled in.** A name alone is not a
  legally valid Impressum under German/EU law (a *ladungsfähige Anschrift* — a real address
  where legal notices can be served — is required). Add it before treating the site as
  fully compliant.
- **`assets/`**
  - `favicon.svg` — graduation-cap icon (Font Awesome Free, CC BY 4.0) on an accent-blue badge.
  - `fonts/` — Open Sans, self-hosted (variable-weight woff2, Latin subset + italic).
  - `profile.jpg`, `cv.pdf`, `dominance-indicators.pdf` — personal assets.
  - `portfolio/` — screenshot thumbnails for the Projects & Initiatives cards (grayscale by
    default, full color on hover): Friends of Medyka, #HackingCorona, Lucilius Interim,
    #LiftUkraine. (There's also a commented-out **Portfolio** section in `index.html` with a
    dedicated card grid for these four — currently disabled but left in place; search for
    `PORTFOLIO (temporarily hidden` to re-enable it.)
- **`cv_winterhager.tex`** — LaTeX source behind `assets/cv.pdf` (not otherwise wired into the site).
- **`.claude/launch.json`** — local dev server config (see below).

## Run locally

```bash
cd vincent-winterhager-cv   # this folder — the GitHub repo itself is named vwinterhager.github.io
python3 -m http.server 8003 --bind 127.0.0.1
# then visit http://localhost:8003
```

## Deployment

Hosted on **GitHub Pages**, served from the `main` branch root of the
`vwinterhager/vwinterhager.github.io` repo (the special GitHub Pages "user site" repo name,
which serves at the bare `https://vwinterhager.github.io/` domain with no path suffix).
Pushing to `main` deploys automatically — no CI/build step needed since it's static HTML.

To take the site offline temporarily: make the repo private (GitHub Free doesn't serve Pages
from private repos, so this fully deprovisions the public site). To bring it back: flip the
repo back to public, then re-enable Pages if it doesn't reactivate on its own —
`gh api -X POST repos/vwinterhager/vwinterhager.github.io/pages -f "source[branch]=main" -f "source[path]=/"`.

## Analytics

None configured. No cookies, no tracking scripts — matches what `privacy.html` discloses.
If that changes, update `privacy.html` accordingly.
