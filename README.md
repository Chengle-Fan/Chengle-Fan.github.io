# Chengle Fan — Personal Academic Website

Source of my personal academic website, built with [Jekyll](https://jekyllrb.com/) and the [al-folio](https://github.com/alshedivat/al-folio) template (v1.x), deployed on GitHub Pages.

- Live site: https://chengle-fan.github.io
- How to add news / projects / publications: see [HOW_TO_UPDATE.md](HOW_TO_UPDATE.md)

## Quick commands

```bash
bundle install              # one-time setup (requires Ruby)
bundle exec jekyll serve    # local preview
```

Deployment is automatic: every push to `main` triggers `.github/workflows/deploy.yml`, which builds the site and publishes it to GitHub Pages.
