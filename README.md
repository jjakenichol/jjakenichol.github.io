# jjakenichol.github.io

Source for my personal academic site, live at **[www.jjakenichol.com](https://www.jjakenichol.com)**.

Built with [Jekyll](https://jekyllrb.com/) on the [al-folio](https://github.com/alshedivat/al-folio) theme (MIT — see `LICENSE`).

## Deploying

Push to `master`. The [`Deploy site`](.github/workflows/deploy.yml) workflow builds the site and
pushes the result to the `gh-pages` branch, which GitHub Pages serves. Nothing to do by hand.

The custom domain comes from `./CNAME` (`www.jjakenichol.com`), which must stay in sync with
`url:` in `_config.yml`.

## What to edit

| To change...                        | Edit                                                 |
| ----------------------------------- | ---------------------------------------------------- |
| Homepage bio                        | `_pages/about.md`                                    |
| Publications                        | `_bibliography/papers.bib` — read the header comments |
| Which papers appear on the homepage | `selected = {true}` on an entry in `papers.bib`       |
| The CV page at `/cv/`               | `assets/json/resume.json` (**not** `_data/cv.yml`)   |
| Downloadable CV PDF                 | `assets/pdf/JakeCV.pdf`                              |
| Software page                       | `_pages/repositories.md` + `_data/repositories.yml`  |
| News items on the homepage          | add a file to `_news/` (copy an existing one)        |
| Publication badge colors            | `_data/venues.yml`                                   |
| Links to coauthors' homepages       | `_data/coauthors.yml`                                |
| Site title, socials, SEO, nav order | `_config.yml`                                        |

### Gotchas worth remembering

- **`assets/json/resume.json` drives `/cv/`, not `_data/cv.yml`.** The theme's CV layout only falls
  back to `_data/cv.yml` when no `resume.json` is loaded, and one always is (via `jekyll_get_json`
  in `_config.yml`). The unused `_data/cv.yml` has been deleted.
- **Never add a `month` field in `papers.bib`.** `jekyll-scholar` leaks that month onto every
  following entry that lacks one, silently stamping wrong dates on later publications. Years alone
  are correct; month-level detail lives in the PDF CV.
- **Your name is bolded via `scholar.last_name` / `scholar.first_name` in `_config.yml`.** If you
  publish under a new spelling of your name, add it to `first_name` or it won't be highlighted.
- Pages are ordered in the navbar by `nav_order` in their front matter; `nav: false` hides a page
  from the navbar but still publishes it at its URL.

## Running locally

Requires Ruby **3.3.3** — `mini_racer` fails to build against the 3.2.2 that rbenv defaults to here:

```sh
RBENV_VERSION=3.3.3 bundle install
RBENV_VERSION=3.3.3 bundle exec jekyll serve
```

Then open <http://localhost:4000>. ImageMagick is required for responsive image generation
(`brew install imagemagick`).

Alternatively, open the repo in the VS Code dev container (`.devcontainer/`), or use Docker:

```sh
docker compose up
```
