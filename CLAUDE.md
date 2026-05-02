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

## Theming — light and dark via CSS variables

Two distinct palettes are defined in `assets/css/extended/custom.css`:
- `:root` — light theme (off-white background, dark green text/accents)
- `:root[data-theme="dark"]` — dark theme (hacker-green on near-black)

PaperMod's theme-init script toggles the `dark` class on `<body>`. `disableThemeToggle = false` in `hugo.toml` renders the toggle button. `defaultTheme = "dark"` means first-visit defaults to dark and writes `pref-theme` to localStorage so the preference persists.

Link and heading colors are driven by `--link-color`, `--link-hover-color`, and `--heading-color` CSS custom properties defined per theme in `custom.css`. Do not hardcode these colors directly on selectors.

## Search

Search uses PaperMod's built-in Fuse.js integration (JS bundled with PaperMod — no CDN). Requirements already in place:

- `home = ["HTML", "RSS", "JSON"]` in `hugo.toml` generates the search index
- `content/search.md` with `layout: "search"` provides the search page

## GitHub Actions deployment

`.github/workflows/hugo.yml` builds with Hugo extended and deploys to GitHub Pages on push to `main`.

- Hugo version is pinned via `HUGO_VERSION` at the top of the workflow file — update it there to upgrade.
- The repository **Pages source** must be set to **GitHub Actions** in repo Settings → Pages.

## Workflow rules

- **Never execute PowerShell commands without explicit user approval first.** Propose the command and wait for confirmation before running it.
- **Never execute Bash commands without explicit user approval first.** Propose the command and wait for confirmation before running it.
- **Never execute git commands.** Git operations are performed manually by the user only.
- **Never ask for confirmation before making CSS modifications.** Just make the change and inform the user it's done.

## JavaScript shipped

| Feature | Status |
|---|---|
| Search (Fuse.js) | Enabled |
| Theme toggle | Enabled (`disableThemeToggle = false`, `defaultTheme = "dark"`) |
| Code copy button | Disabled (`ShowCodeCopyButtons = false`) |
| Scroll-to-top | Disabled (`ShowScrollToTop = false`) |
| Share buttons | Disabled (`ShowShareButtons = false`) |
