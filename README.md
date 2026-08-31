# Personal Website | Andy Man Yeung Tai

Portfolio and academic website: **https://andytai7.github.io/Andy-Tai/**

Built with [Jekyll](https://jekyllrb.com/) using the [al-folio](https://github.com/alshedivat/al-folio) theme, deployed via GitHub Actions to GitHub Pages.

## Local development

```sh
bundle install
bundle exec jekyll serve
# browse http://localhost:4000/Andy-Tai/
```

## Deployment

Pushing to `main` runs `.github/workflows/deploy.yml`, which builds the site and publishes it to the `gh-pages` branch. In the repository's **Settings → Pages**, set the source to *Deploy from a branch → gh-pages* (one-time setup).

## Content

- `_pages/` : about, publications, projects, CV, news pages
- `_projects/` : project cards + detail pages
- `_bibliography/papers.bib` : publications (rendered by jekyll-scholar)
- `_news/` : homepage announcements
- `assets/json/resume.json` : structured CV data (JSON Resume) for the CV page
- `assets/pdf/` : downloadable `cv.pdf` and `resume.pdf`
- `assets/img/` : profile photo, favicon, project images
- `_data/socials.yml` : social links shown on the about page

## Previous site

The former Quarto-based site was fully replaced in commit `ff7daa5`; its history remains in git (`git checkout 16e0d66` to view the old source).
