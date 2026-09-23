# whthissell.github.io

Source for William Thissell's engineering portfolio, live at
https://whthissell.github.io/.

## Structure

- `_config.yml`: site settings (name, tagline, LinkedIn handle, resume path, nav)
- `index.md`: home page intro; the project grid is generated from `_projects/`
- `about.md`, `resume.md`: static pages
- `_projects/`: one Markdown file per project, each rendered at `/projects/<slug>/`.
  `order` in the front matter sets its position on the home page.
- `_layouts/`, `_includes/`: templates (custom, no third-party theme)
- `assets/css/main.scss`: all styling
- `assets/images/covers/`: project card artwork
- `assets/William_Thissell_Resume.pdf`: the resume shown on `/resume/`

## Updating the resume

Replace `assets/William_Thissell_Resume.pdf`, then regenerate the phone preview image:

```bash
pdftoppm -png -r 110 -singlefile assets/William_Thissell_Resume.pdf assets/images/resume-preview
```

## Local preview

```bash
bundle install
bundle exec jekyll serve
```

## Deploying

Every push to `main` builds and deploys through `.github/workflows/pages.yml`
(GitHub Actions, Pages source set to "GitHub Actions").
