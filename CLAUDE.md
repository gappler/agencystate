# Project Rules — agency-state

This is the **public** repo for the Agency State marketing site (agencystate.ai). It is served by GitHub Pages and anything committed here is publicly visible.

Internal content lives in two private companion repos: curriculum, pricing, research, and strategy in [`agency-state-curriculum`](https://github.com/gappler/agency-state-curriculum), and brand + outbound comms in [`agency-state-publishing`](https://github.com/gappler/agency-state-publishing). If you need to read or edit brand rules, session designs, pricing strategy, or internal research, work in the appropriate private repo — not this one.

## Current state (April 2026)

The site is on a holding page. Cohort 1 of the Annual Planning Cohort is being prepared for the week of July 13, 2026. The previous cohort page work is preserved on the `cohort-v1-paused` branch in the agency-state repo.

## Repo Layout

- `index.html` — single-page marketing site
- `assets/` — wordmark, mark, and og-image files (`.svg`, `.png`); Illustrator source files in `assets/illustrator files/`
- `CNAME` — GitHub Pages custom domain

## Brand

Brand decisions are settled by the brand book in `agency-state-publishing/brand/agency-state-brand-book.md`. Read it before writing or editing any copy on this site. Do not restate brand rules here.

## Strategy

Strategic decisions — audience, offer, format, pricing — are settled by `agency-state-curriculum/strategy/agency-state-brief-v2.md`. Read it before editing site copy related to the cohort offer.

## Document Conventions

- Generated markdown documents should include a YAML frontmatter header (title, date, version, status) per global preferences.
- Track versions inside files via frontmatter, not in filenames.
- New files: prefer lowercase with hyphens.

## Git Discipline

- **This repo is public.** Never commit internal content here. Curriculum, pricing, and research live in `agency-state-curriculum`; brand and outbound drafts live in `agency-state-publishing`.
- Commit in focused, descriptive units. Don't let unrelated changes pile up in one commit.
- Write commit messages that explain the *why*, not just the *what*.
- Don't commit `.DS_Store` or other macOS cruft (already in `.gitignore`).

## Website Changes

- `index.html` is hand-authored — no build step. Edit directly.
- Before claiming a visual change is done, open `index.html` in a browser and verify it renders as intended. Type-checking doesn't exist here; your eyes are the test suite.
- Keep the footer domain, nav CTA, and hero CTA in sync if any of them change.
