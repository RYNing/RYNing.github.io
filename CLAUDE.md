# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal academic homepage for Ruining Yang, deployed via GitHub Pages at https://ryning.github.io. It is built on the [Academic Pages](https://github.com/academicpages/academicpages.github.io) Jekyll template (itself derived from Minimal Mistakes). Most of the repo is unmodified template code; the site-specific content is concentrated in a few files (see below). There are no tests or linters.

## Commands

```bash
bundle install                               # install Ruby deps (delete Gemfile.lock and retry on errors)
bundle exec jekyll serve -l -H localhost     # serve at localhost:4000 with livereload
docker compose up                            # alternative: run in Docker (uses _config_docker.yml override)
npm run build:js                             # only needed if editing assets/js/*; regenerates assets/js/main.min.js
```

Changes to `_config.yml` require restarting `jekyll serve`. Deployment is automatic: GitHub Pages builds from `master` on push.

## Architecture: where the real site lives

The entire site is effectively a **single page** — `_pages/about.md` (permalink `/`). It contains:
- Hand-written HTML sections (About, Education, Experience, Publications — in that order, mirroring the sibling site) with `id` anchors.
- A Liquid loop that renders every item in the `publications` collection as a "paper-box" card.
- An inline `<style>` block at the bottom holding the custom styling for the home page (layout width/padding, paper cards, timeline). Home-page style tweaks go here, not in `_sass/`.

The top nav (`_data/navigation.yml`) links to anchors on that page (`/#education`, `/#experience`, `/#publications`), so section `id`s in `about.md` must stay in sync with it.

Sidebar profile info (name, avatar, email, Scholar, GitHub) comes from the `author:` block in `_config.yml`. Research Interests also live in the sidebar: the list is `author.interests` in `_config.yml`, rendered by `_includes/author-profile.html` and styled at the end of `_sass/layout/_sidebar.scss`.

### Publications (`_publications/*.md`)

Each file is front matter only; the body is unused. Fields consumed by the `about.md` loop:
- `title`, `venue` (rendered as a non-link badge), `citation` (inline HTML: co-authors wrapped in grey `<span style='color:#7a8288;'>`, the site owner as `<b>Ruining Yang</b>`, `<sup>*</sup>` for equal contribution, `<sup>†</sup>` for corresponding author — take these marks from the arXiv first page; the legend sits at the end of the Publications heading line)
- `sort_order` — integer controlling display order (ascending); the `date` / filename is **not** used for ordering
- `teaser` — filename in `images/` (falls back to `images/paper-placeholder.svg`)
- `paperurl`, `projecturl` — optional links
- `coderepo` (`owner/repo`, drives the GitHub stars badge) together with `codeurl`
- `award` — optional, rendered in bold red above the description (e.g. `🏆 Best Paper Award`)
- `highlight` — optional one-liner rendered in orange (e.g. nuReasoning's dataset-series note)
- `description` — optional short blurb
- `published: false` hides an entry without deleting it

When adding a publication, pick a `sort_order` and renumber others as needed so the sequence stays contiguous.

### Other customizations

- Education/Experience entries use `<ul class="timeline with-logos">` with a 44px square logo from `images/logos/`.
- Organization names in the About text are plain text (no link) with a small logo in front (`img.inline-logo`, the style used on cancui19.github.io). The logo and the first word are wrapped in `<span class="nowrap">` so the logo never ends a line by itself.
- This site is kept visually in sync with the sibling repo `../Bobchenyx.github.io` (same paper-box, venue badge, timeline-with-logos and author-mark conventions); shared papers and logos can be copied from there. Unlike that repo, this one hardcodes light-theme colors instead of CSS variables.
- Dark mode is disabled: the toggle was removed from `_includes/masthead.html` and `_includes/head/custom.html` forces the light theme.
- Site search is off (`search: false`).

## Conventions

Commit messages use a `type: summary` prefix — `content:` (text/bio changes), `style:` (CSS), `feat:` (new elements such as teaser images), `chore:` (reordering, hiding entries, housekeeping).
