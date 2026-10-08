# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal academic homepage for Ruining Yang, deployed via GitHub Pages at https://ryning.github.io. It is built on the [Academic Pages](https://github.com/academicpages/academicpages.github.io) Jekyll template (itself derived from Minimal Mistakes). Most of the repo is unmodified template code; the site-specific content is concentrated in a few files (see below). There are no tests or linters.

## Commands

Use **Ruby 3.3**, the version GitHub Pages builds with. Install it with `brew install ruby@3.3`; it is keg-only, so put it on PATH first in each shell: `export PATH=/opt/homebrew/opt/ruby@3.3/bin:$PATH`. The macOS system Ruby 2.6 can't install `github-pages`. Ruby 4.0 (Homebrew's default `ruby`) makes bundler fall back to an old `github-pages` (223, with Liquid 4.0.3), which then fails at startup. Gems install into the gitignored `vendor/bundle` (one-time setup: `bundle config set --local path vendor/bundle`).

```bash
bundle install                               # install Ruby deps (delete Gemfile.lock and retry on errors)
bundle exec jekyll serve -l -H localhost     # serve at localhost:4000 with livereload
bundle exec jekyll serve -l -H localhost --unpublished   # also render `published: false` publications
docker compose up                            # alternative: run in Docker (uses _config_docker.yml override)
npm run build:js                             # only needed if editing assets/js/*; regenerates assets/js/main.min.js
lsof -ti:4000 -sTCP:LISTEN | xargs kill      # stop a backgrounded server
```

Changes to `_config.yml` require restarting `jekyll serve`. Deployment is automatic: GitHub Pages builds from `master` on push.

## Architecture: where the real site lives

The site has three hand-written pages in `_pages/`. The top nav (`_data/navigation.yml`) has Home (`/`), Experience and Publications; Education is deliberately not in the nav. `_includes/masthead.html` never highlights a nav item that links to `/`, so on the home page the site title "Ruining Yang" is highlighted instead of Home. On phones (<600px, rules at the end of the masthead section in `_sass/layout/_masthead.scss`):
- The Home item is hidden.
- The site title reads "Ruining Yang (Home)" on every page except the home page.
- Nav text is 15px with tighter gaps, so Experience and Publications both fit down to 360px wide.
- The greedy-nav hamburger button starts with `class="hidden"`. Otherwise the script reserves room for the button on load and folds Publications into the menu.
- `about.md` (permalink `/`, the home page): About, Education, Experience, then Selected Publications — in that order, mirroring the sibling site. Education is written inline here and has no page of its own. Selected Publications is a loop over publications that are not `selected: false`, ordered by `sort_order`; the "See All Publications >" link in its heading goes to `/publications/`.
- `experience.md` (`/experience/`): the same timeline as the home page's Experience section, plus each internship's supervisors and work. Both render `_includes/experience.html`, so edit entries there, not in the pages. The page passes `details=true` to show the `timeline-desc` lines. The home page leaves them out and instead shows a "More Details >" link to `/experience/` in the heading, styled like "See All Publications >". The About text does not mention internships, which live only here. Below the timeline, `experience.md` itself holds an Academic Service section that appears only on this page, with "As an Organizer" and "As a Reviewer" lists, newest first.
- `publications.md` (`/publications/`): every publication, ordered by `all_order`.

The two publication pages render each paper with `_includes/paper-box.html`. All three pages include `_includes/page-styles.html`, the shared `<style>` block (layout width/padding, paper cards, timeline). Page style tweaks go in that include, not in `_sass/`.

Sidebar profile info (name, avatar, email, Scholar, GitHub) comes from the `author:` block in `_config.yml`. Research Interests also live in the sidebar: the list is `author.interests` in `_config.yml`, rendered by `_includes/author-profile.html` and styled at the end of `_sass/layout/_sidebar.scss`.

### Publications (`_publications/*.md`)

Each file is front matter only; the body is unused, and the filename prefix is just a per-year sequence number. Fields consumed by `paper-box.html` and the two page loops:
- `title`, `venue` (rendered as a non-link badge), `citation` (inline HTML: co-authors wrapped in grey `<span style='color:#7a8288;'>`, the site owner as `<b>Ruining Yang</b>`, `<sup>*</sup>` for equal contribution, `<sup>†</sup>` for corresponding author — take these marks from the paper's first page (arXiv or CVF Open Access); the legend sits at the end of each Publications heading line)
- `sort_order` — integer controlling the home page order (ascending)
- `all_order` — integer controlling the `/publications/` order (ascending). The two orders are curated separately: the home page puts Post-Training first, the full list puts SpanVLA first.
- `date` — when the paper was published: the conference's start date for accepted papers, arXiv v1 date for preprints. Not used for ordering. Future dates are fine (`future: true`).
- `selected: false` — leave the paper off the home page; it still appears on `/publications/`
- `teaser` — filename in `images/` (falls back to `images/paper-placeholder.svg`). Usually the paper's Figure 1, cropped from the PDF.
- `paperurl`, `projecturl` — optional links
- `coderepo` (`owner/repo`, drives the GitHub stars badge) together with `codeurl`
- `award` — optional, rendered in bold red above the description (e.g. `🏆 Best Paper Award`)
- `highlight` — optional one-liner rendered in orange (e.g. nuReasoning's dataset-series note)
- `description` — optional short blurb
- `published: false` hides an entry from both pages without deleting it

When adding a publication, set `date`, pick both a `sort_order` and an `all_order`, and renumber others as needed so each sequence stays contiguous. Entries with `selected: false` keep their `sort_order` slot, so that numbering covers all files together. `/publications/` lists everything on Google Scholar except four papers that are deliberately left out: DTbot, Sina Weibo rumor detection, "From Static to Dynamic: a Survey of Topology-Aware Perception in Autonomous Driving", and "Unsupervised Search for Ethnic Minorities' Medical Segmentation Training Set".

### Other customizations

- Education/Experience entries use `<ul class="timeline with-logos">` with a 44px square, framed logo from `images/logos/`, aligned to the top of the entry.
- Organization names in the About text are plain text (no link) with a small logo in front (`img.inline-logo`, the style used on cancui19.github.io). The logo and the first word are wrapped in `<span class="nowrap">` so the logo never ends a line by itself.
- This site is kept visually in sync with the sibling repo `Bobchenyx/Bobchenyx.github.io` (same paper-box, venue badge, timeline-with-logos and author-mark conventions); shared papers and logos can be copied from there. It is not necessarily cloned locally — clone it next to this repo (`../Bobchenyx.github.io`) if needed. Unlike that repo, this one hardcodes light-theme colors instead of CSS variables.
- Dark mode is disabled: the toggle was removed from `_includes/masthead.html` and `_includes/head/custom.html` forces the light theme.
- Site search is off (`search: false`).
- Mobile layout follows the sibling site's "Fix mobile layout of homepage" commit:
  - The extra `#main` left padding in `page-styles.html` applies only at ≥64em; phones keep the theme's narrow gutter.
  - Paper cards stack below 600px, with the teaser at full width.
  - The footer is `position: absolute` at the end of the page, not fixed to the viewport (`_sass/layout/_footer.scss`).
  - `.author__name` uses `word-break: keep-all` so "(杨蕊宁)" never splits.
- To check phone widths, don't use headless Chrome's `--window-size`: the viewport never goes below 500px. Use DevTools device emulation instead (`Emulation.setDeviceMetricsOverride` with `mobile: true`, e.g. 390px). For the masthead, use viewport-only screenshots: a full-page capture (`captureBeyondViewport`) resizes the viewport, re-runs greedy-nav, and can show items folded into the menu that real phones show.
- Template leftovers that this site does not use: `talkmap*`, `scripts/` (CV JSON generation), `_data/cv.json`, and `.github/workflows/` (talk scraping and PR cleanup). Leave them alone unless asked.

## Conventions

Commit messages use a `type: summary` prefix — `content:` (text/bio changes), `style:` (CSS), `feat:` (new elements such as teaser images), `chore:` (reordering, hiding entries, housekeeping).
