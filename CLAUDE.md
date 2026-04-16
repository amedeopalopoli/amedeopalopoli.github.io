# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Personal website for Amedeo Palopoli (amedeopalopoli.com), built with **Hugo** using the `hugo-resume` theme (included as a git submodule in `themes/hugo-resume/`). Deployed automatically to GitHub Pages via GitHub Actions on every push to `main`.

## Commands

```bash
# Serve locally with live reload
hugo server

# Build for production
hugo --minify

# Create new content using archetypes
hugo new blog/post-name.md
hugo new projects/creations/project-name.md
hugo new projects/contributions/project-name.md
hugo new publications/pub-name.md
```

## Architecture

Content is driven by two mechanisms:

**Data files** (`data/*.json`) — structured data rendered directly on the homepage by the theme:
- `data/skills.json` — skill groups shown on the skills section
- `data/experience.json` — work history
- `data/education.json` — academic background
- `data/certifications.json` — professional certifications
- `data/publications.json` — academic/technical publications (also renders at `/publications/`)
- `data/talks.json` — conference talks (renders at `/talks/`)
- `data/boards.json` — board memberships

**Markdown content** (`content/`) — richer pages with full layout support:
- `content/_index.md` — homepage bio/summary text
- `content/blog/` — blog posts
- `content/skills/_index.md`, `content/contact/index.md`, `content/search.md` — section pages

## Site configuration

`hugo.toml` controls which sections appear via `params.sections`. To show/hide a section (e.g. boards, certifications), toggle the corresponding boolean params (`showBoards`, `showCertifications`, etc.) or edit the `sections` array.

## Deployment

Push to `main` → GitHub Actions builds with `hugo --minify` and deploys to the `gh-pages` branch. The workflow uses `PERSONAL_TOKEN` secret. The custom domain `amedeopalopoli.com` is set via the workflow's `cname` parameter.

The theme is loaded as a **git submodule** (`themes/hugo-resume`). When cloning, use `--recurse-submodules` or run `git submodule update --init`.
