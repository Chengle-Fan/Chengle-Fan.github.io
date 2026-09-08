# Agent Guidelines — Chengle Fan's academic website

This repo is a **personal academic website** built from the [al-folio](https://github.com/alshedivat/al-folio) v1.x starter. The template's contributor tooling (tests, dev workflows, docs/, docker) has been removed; only what the site needs remains.

## What lives where

| Content | Edit |
| --- | --- |
| Site-wide settings (name, url, features) | `_config.yml` |
| Homepage bio / research interests | `_pages/about.md` |
| News items | `_news/*.md` (one file per item) |
| Research projects | `_projects/*.md` + images in `assets/img/projects/<name>/` |
| Publications | `_bibliography/papers.bib` |
| CV page data | `_data/cv.yml` (rendercv format) |
| Social links | `_data/socials.yml` |

See `HOW_TO_UPDATE.md` (Chinese) for the day-to-day maintenance cheat sheet.

## Hard rules

- `_config.yml`: keep `url: https://chengle-fan.github.io` and `baseurl` **blank** — the site deploys to the root of GitHub Pages. A non-blank baseurl breaks all styling.
- `Gemfile` and `_config.yml` `plugins:` must list the same plugins — a plugin present in only one is silently inert.
- Do not add `_layouts/`, `_includes/`, or `_sass/` unless intentionally overriding the theme gems (`al_folio_core` etc.). Record any such override.
- Layouts/includes are provided by pinned gems in the `Gemfile`; bump versions there rather than copying theme internals into this repo.

## Validate

```bash
bundle install
bundle exec jekyll build   # must complete without errors
```

Deployment: push to `main` triggers `.github/workflows/deploy.yml` (Ruby 3.3 + Node 20 + ImageMagick + purgecss) and publishes `_site` to GitHub Pages.
