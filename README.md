# Portfolio site

A Jekyll site for showcasing engineering projects — built as a lighter-weight,
more visual alternative to a one-page resume, aimed at engineering and
management-consulting internship applications.

## Structure

- `_config.yml` — site settings (**update the TODOs before deploying** — see below)
- `index.md` — home page (hero + project grid)
- `about.md`, `resume.md` — static pages
- `_projects/` — one file per project; each becomes a page at `/projects/<slug>/`
- `_layouts/`, `_includes/` — templates (custom-built, no external theme)
- `assets/css/main.scss` — all site styling, single file, no framework
- `.github/workflows/pages.yml` — builds and deploys to GitHub Pages via GitHub Actions

## Local development

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

## Before you deploy — TODOs

1. In `_config.yml`, set `url`, `baseurl`, and `github_username` (see the comments
   there for the two cases: a `<username>.github.io` user site vs. a project repo).
2. Add a real resume PDF at `assets/resume.pdf` and link it from `resume.md`.
3. Flesh out `_projects/vtol-drone.md` and `_projects/ai-in-finance.md` — they're
   drafted from what's known so far; replace the bracketed placeholders with real
   details, numbers, and images.
4. Add project cover images to `assets/images/` and set each project's
   `cover_image` front-matter field.
5. Add more entries to `_projects/` for any other projects you want to showcase —
   copy the front matter from an existing one.

## Deploying to GitHub Pages

1. Create a new repo on GitHub (either `<your-username>.github.io` for a user site,
   or any name for a project site).
2. Push this code to the `main` branch:
   ```bash
   git remote add origin <your-repo-url>
   git branch -M main
   git push -u origin main
   ```
3. In the repo's **Settings → Pages**, set **Source** to **GitHub Actions**. The
   included workflow (`.github/workflows/pages.yml`) will build and deploy the site
   automatically on every push to `main`.
