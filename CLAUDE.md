# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Hugo static site using the PaperMod theme, deployed to GitHub Pages at `https://0xremyruiz.github.io`. Content is in English. Three content sections: `writeups`, `projects`, `notes`.

## Commands

```bash
# Serve locally with live reload (requires Hugo extended)
hugo server -D

# Production build
hugo --gc --minify

# New post (uses archetypes/default.md)
hugo new writeups/my-post.md
hugo new projects/my-project.md
hugo new notes/my-note.md
```

## PaperMod theme (git submodule)

PaperMod lives at `themes/PaperMod/` as a git submodule. After cloning the repo:

```bash
git submodule update --init --recursive
```

To update PaperMod to the latest commit:

```bash
git submodule update --remote themes/PaperMod
git add themes/PaperMod
git commit -m "update PaperMod"
```

## Dark mode — CSS-only, no localStorage

Dark mode is enforced purely through `assets/css/extended/custom.css`, which overrides PaperMod's color variables at both `:root` and `.dark`. The palette is therefore constant regardless of which class the body carries.

`disableThemeToggle = true` in `hugo.toml` prevents the toggle button from rendering. PaperMod's theme-init script still runs on each page, but since the toggle is disabled the `pref-theme` localStorage key is never written — its read returns `null` and is a no-op.

Do not remove the dual `:root, .dark { ... }` block from `custom.css` without replacing the theming strategy.

## Search

Search uses PaperMod's built-in Fuse.js integration (JS bundled with PaperMod — no CDN). Requirements already in place:

- `home = ["HTML", "RSS", "JSON"]` in `hugo.toml` generates the search index
- `content/search.md` with `layout: "search"` provides the search page

## GitHub Actions deployment

`.github/workflows/hugo.yml` builds with Hugo extended and deploys to GitHub Pages on push to `main`.

- Hugo version is pinned via `HUGO_VERSION` at the top of the workflow file — update it there to upgrade.
- The repository **Pages source** must be set to **GitHub Actions** in repo Settings → Pages.

## JavaScript shipped

| Feature | Status |
|---|---|
| Search (Fuse.js) | Enabled |
| Theme toggle | Disabled (`disableThemeToggle = true`) |
| Code copy button | Disabled (`ShowCodeCopyButtons = false`) |
| Scroll-to-top | Disabled (`ShowScrollToTop = false`) |
| Share buttons | Disabled (`ShowShareButtons = false`) |
