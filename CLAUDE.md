# Project Rules — agency-state

This is the **public** repo for the Agency State marketing site (agencystate.ai). It is served by GitHub Pages and anything committed here is publicly visible.

Curriculum, brand book, notes, and research live in the private companion repo [`agency-state-private`](https://github.com/gappler/agency-state-private). If you need to read or edit brand rules, session designs, pricing strategy, or internal research, work in that repo — not this one.

## Repo Layout

- `index.html` — single-page marketing site
- `assets/` — wordmark, mark, and og-image files (`.svg`, `.png`); Illustrator source files in `assets/illustrator files/`
- `CNAME` — GitHub Pages custom domain

## Brand

Brand decisions are settled by the brand book in the private repo (`agency-state-private/brand/agency-state-brand-book.md`). Read it before writing or editing any copy on this site. Do not restate brand rules here.

## Document Conventions

- Generated markdown documents should include a YAML frontmatter header (title, date, version, status) per global preferences.
- Track versions inside files via frontmatter, not in filenames.
- New files: prefer lowercase with hyphens.

## Git Discipline

- **This repo is public.** Never commit internal content (curriculum, pricing strategy, brand book, notes, research) here. Those belong in `agency-state-private`.
- Commit in focused, descriptive units. Don't let unrelated changes pile up in one commit.
- Write commit messages that explain the *why*, not just the *what*.
- Don't commit `.DS_Store` or other macOS cruft (already in `.gitignore`).

## Website Changes

- `index.html` is hand-authored — no build step. Edit directly.
- Before claiming a visual change is done, open `index.html` in a browser and verify it renders as intended. Type-checking doesn't exist here; your eyes are the test suite.
- Keep the footer domain, nav CTA, and hero CTA in sync if any of them change.
