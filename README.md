# ferdinand-genans.github.io

Source of my personal academic website: <https://ferdinand-genans.github.io/>.

## Stack

- [Hugo](https://gohugo.io/) (extended) + the
  [Hugo Blox / Academic CV](https://github.com/HugoBlox/theme-academic-cv) theme,
  pulled as a Hugo module via `go.mod`.
- Deployed automatically on every push to `main` by
  [.github/workflows/publish.yaml](.github/workflows/publish.yaml)
  (builds with Hugo + `actions/deploy-pages`).

> **GitHub Pages source must be set to "GitHub Actions"** (Settings → Pages → Source).
> If it is set to "Deploy from a branch" instead, GitHub will serve this README
> through Jekyll instead of the built Hugo site.

## Content layout

| Path | What it holds |
|------|---------------|
| [content/_index.md](content/_index.md) | Home page (biography hero + News, rendered by an override of the `resume-biography-3` blox) |
| [content/authors/admin/_index.md](content/authors/admin/_index.md) | My profile (drives the home hero and the Resume page) |
| [content/resume/_index.md](content/resume/_index.md) | Resume page (download CV + rendered experience / skills / awards / languages + embedded PDF preview) |
| [content/research/_index.md](content/research/_index.md) | Research page (publications + preprints as cards) |
| [content/research/papers-illustrations/](content/research/papers-illustrations/) | Small thumbnail per publication |
| [content/blog/](content/blog/) | Blog section (currently **hidden** — `build: render: never` until I have posts ready) |
| [data/news.yaml](data/news.yaml) | News items shown on the home page (newest first) |
| [data/publications.yaml](data/publications.yaml) | Publications + preprints rendered on the research page |
| [layouts/shortcodes/](layouts/shortcodes/) | `publication_list` and `latest_news` shortcodes |
| [layouts/partials/blox/](layouts/partials/blox/) | Project overrides of `resume-biography-3` and `resume-languages` |
| [assets/css/custom.css](assets/css/custom.css) | Wider content area on Resume/Research, publication thumbnail sizing, news-in-hero styling |
| [static/uploads/CV_FGenans_DS.pdf](static/uploads/CV_FGenans_DS.pdf) | CV file served at `/uploads/CV_FGenans_DS.pdf` |

## Local development

```bash
# Run dev server
hugo server --port 1313 --disableFastRender

# Production build (what the GitHub workflow does)
hugo --gc --minify
```

## Common edits

- **Add a news item** → append to [data/news.yaml](data/news.yaml).
- **Add a publication** → append an entry under `publications:` or `preprints:` in
  [data/publications.yaml](data/publications.yaml), and drop a thumbnail into
  [content/research/papers-illustrations/](content/research/papers-illustrations/).
- **Update CV info** → edit [content/authors/admin/_index.md](content/authors/admin/_index.md)
  (the Resume page reads from it) **and** replace
  [static/uploads/CV_FGenans_DS.pdf](static/uploads/CV_FGenans_DS.pdf) with a fresh PDF.
- **Unhide the Blog** → remove the `build` / `cascade` blocks from
  [content/blog/_index.md](content/blog/_index.md) (and from the sample post),
  then uncomment the Blog entry in [config/_default/menus.yaml](config/_default/menus.yaml).

## Adding a notebook-style blog post

1. Write the post in Jupyter under `content/blog/<slug>/notebook.ipynb`.
2. Convert to Markdown next to it: `jupyter nbconvert --to markdown notebook.ipynb --output index`.
3. Add YAML front matter to `index.md` (`title`, `date`, `summary`, `authors: [admin]`, optional `tags`).
4. Drop referenced figures (e.g. `plot.svg`, `output_5_0.png`) into the same folder —
   Hugo picks them up as page resources.
5. The raw `.ipynb` is ignored by Hugo (`ignoreFiles` in `config/_default/hugo.yaml`).
