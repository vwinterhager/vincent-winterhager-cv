# Vincent Winterhager — personal academic site

Two things are in this folder:

1. **`index.html`** — a working, self-contained prototype of your site. Double-click it to
   open in any browser. No build step, no dependencies. It has all your sections (About,
   Publications, Talks & Teaching, Writing, Projects, CV, Contact), a clean academic style,
   and a dark-mode toggle (the ◐ button, top right). Edit the text directly — everything
   marked *[edit: ...]* is a placeholder.
2. **This README** — the runbook for standing up the real **Hugo Blox Academic CV**
   version (the stack you chose), which needs internet access and so has to run on your
   own machine, not in this session's sandbox.

Use the prototype as an instant preview / fallback, and follow the steps below for the
production Hugo Blox site.

---

## A. Run the prototype (30 seconds)

Just open `index.html`. To serve it like a real site (nicer for testing links):

```bash
cd this-folder
python3 -m http.server 8000
# then visit http://localhost:8000
```

To put the `VW` avatar circle to use, drop a photo at `assets/profile.jpg` and a
`assets/cv.pdf` for the CV download button.

---

## B. Stand up the Hugo Blox Academic CV site (your chosen stack)

Prerequisites (one-time):

- **Git** — you have it.
- **Hugo *extended*** — required (the plain build won't work). macOS: `brew install hugo`.
  Windows: `winget install Hugo.Hugo.Extended`. Then check: `hugo version` should show
  `+extended`.
- **Go** — needed because Hugo Blox is delivered as Hugo Modules. Install from
  https://go.dev/dl/ and confirm with `go version`.

### 1. Get the starter

Open the template and click **“Use this template” → Create a new repository**:

> https://github.com/HugoBlox/theme-academic-cv

Then clone *your* new repo and run it:

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
hugo server
# open the http://localhost:1313 URL it prints
```

`hugo server` live-reloads as you edit — that's your real working local version.

> ⚠️ Version note: the project was renamed from **Wowchemy/Academic** to **Hugo Blox**.
> Only follow docs at **https://docs.hugoblox.com** and ignore older "Wowchemy" tutorials —
> mixing the two is the single most common source of setup errors.

### 2. Make it yours — the files that matter

| What | Where |
|------|-------|
| Name, role, social links, photo | `content/authors/admin/_index.md` + `avatar.jpg` |
| Homepage sections shown & order | `content/_index.md` |
| Site title, menu, colour theme | `config/_default/` (`params.yaml`, `menus.yaml`) |
| Publications (auto from BibTeX) | `content/publication/` — or import a `.bib` |
| Talks | `content/event/` |
| Teaching / courses | add a `content/teaching/` section |
| Blog posts | `content/post/` |
| Projects | `content/project/` |
| CV PDF download | `static/uploads/cv.pdf`, link it in the author file |

### 3. Import your publications (the big time-saver)

Export a BibTeX file from Google Scholar / Zotero, then:

```bash
hugoblox import bibtex my-publications.bib
# (older command name: `academic import`)
```

Each entry becomes a publication page with DOI, abstract, and a “Cite” button.

### 4. Pick the clean-academic look

In `config/_default/params.yaml` set a light, minimal theme (e.g. `theme: minimal`
or `ocean`) and a serif heading font. Browse options in the HugoBlox docs under
*Appearance*.

### 5. Deploy for free

With Git already in hand, easiest paths:

- **GitHub Pages** — push to GitHub; enable Pages with a Hugo Actions workflow (the
  starter often includes `.github/workflows/`).
- **Cloudflare Pages / Netlify** — connect the repo, set build command `hugo --gc --minify`,
  output dir `public`. Auto-deploys on every push.

Point your custom domain at it when ready.

---

## Reference links

- Starter template: https://github.com/HugoBlox/theme-academic-cv
- Docs: https://docs.hugoblox.com
- Hugo Blox home: https://hugoblox.com
