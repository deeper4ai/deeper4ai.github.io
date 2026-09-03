# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The public website for the DEEPER project (AI guidance for automated theorem
provers), a joint effort between University of Melbourne and Czech Technical
University in Prague. Built with [Hugo](https://gohugo.io/) using the
`beautifulhugo` theme, deployed via GitHub Pages.

## Repo layout

- `src/` — Hugo source. All editing happens here.
  - `src/content/` — the actual page content (Markdown/TOML frontmatter).
    - `_index.md` — homepage (project description, goals, funding, partnership).
    - `news/` — one file per news post (see below).
    - `publications.md` — single page listing all papers, organized by section
      (Conference Papers, Preprints, ...).
    - `team.md` — team listing, grouped by institution.
    - `products.md` — software/tool listings, grouped by product name.
    - `papers/` — PDF files linked from `publications.md`.
    - `download/` and `images/` — static assets linked from content; these are
      gitignored (see `src/.gitignore`) so they exist locally but aren't
      committed — check before assuming a referenced asset is tracked.
  - `src/config.toml` — site config: title, menu structure, base URL.
  - `src/Makefile` — build entry points.
- `docs/` — Hugo's generated static output. This is the actual published site
  (GitHub Pages serves from `docs/`). It is committed to the repo and must be
  regenerated (via `hugo`) and committed alongside any content change.

## Workflow

1. Edit files under `src/content/*.md`.
2. Run `hugo` from within `src/` (via `make` or directly) to regenerate `docs/`.
3. Commit both the `src/` changes and the regenerated `docs/` output, then push.

```
cd src && make        # runs `hugo`, regenerates docs/
cd src && make test   # `hugo server -D --disableFastRender`, local preview with drafts
```

The site deploys automatically on push — there is no separate CI/build step,
so `docs/` must always be regenerated and committed before pushing.

## Adding a news post

Create a new file under `src/content/news/`, e.g. `some-slug.md`:

```
+++
date = '2026-08-13T10:00:00+02:00'
title = "📚 Emoji-prefixed headline"
subtitle = "One-sentence summary shown in listings"
author = "Deeper4AI @ Melbourne"   # or "@ Prague", per institution
tags = ["Publications", "SomeTopic", ...]
+++

Body text. Use _italics_ for names, [links](url) for venues/people,
and `+` bullet lists for enumerating multiple items (e.g. multiple papers).
```

Filenames are slugs (no ordering prefix); Hugo sorts the news list by `date`.

## Adding a publication

Publications all live in the single `src/content/publications.md` file, under
one of the existing `##` sections (Conference Papers, Preprints). Follow the
existing numbered-list entry format exactly:

```
N. _Author One_, _Author Two_:\
   **✦ Paper Title**.\
   In <venue details>, [Venue Name YY](venue-url).\
   [ [pdf](/papers/xxx.pdf) |
     [doi](https://doi.org/...) |
     [proceedings](...) |
     [bibtex](...)
   ]
```

Note the trailing `\` for hard line breaks (required by the theme's Markdown
rendering), and that PDFs referenced as `/papers/xxx.pdf` must be added to
`src/content/papers/`. Preprint entries typically link `arXiv`/`dblp`/`bibtex`
instead of `doi`/`proceedings`, and may append `(Accepted to [Venue](...))`
when only a PDF is available yet (no DOI/proceedings).

Corresponding news posts (announcing new publications) are common practice
alongside adding entries here — check the last few `git log` entries for the
paired pattern of "add papers" + "news" commits.

### Pending follow-up

The PAAR'26 paper ("Agent Hunt: Bounty Based Collaborative Autoformalization
With LLM Agents", CEUR-WS Vol-4241) currently has its `bibtex` link pointing
at the arXiv/CoRR DBLP record, since DBLP hasn't indexed the `conf/paar`
proceedings entry yet. Once it appears on DBLP, update that `bibtex` (and
ideally add a `doi` if CEUR-WS assigns one) to point at the proper `conf/paar`
record.

## Conventions

- Emoji prefixes are used throughout for visual scanning: news titles, section
  headers (`## 📚 Conference Papers`), and product entries (`🔔`). Match
  existing usage when adding entries rather than inventing new symbols.
- Country flag emoji mark institutional affiliation (🇦🇺 Melbourne, 🇨🇿 Prague)
  in `team.md` and `_index.md`.
- Frontmatter dates use Hugo's TOML format `'YYYY-MM-DDTHH:MM:SS+TZ'`.
