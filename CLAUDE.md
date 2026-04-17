# Project Rules — agency-state

This repo holds the Agency State website, brand system, and strategic research.

## Repo Layout

- `index.html` — single-page marketing site (agencystate.ai)
- `brand/` — brand book (copy/voice/positioning tiebreaker) and brand guidelines (visual identity)
- `assets/` — wordmark, mark, and og-image files (`.svg`, `.png`); Illustrator source files in `assets/illustrator files/`
- `docs/` — pricing strategy, cohort curriculum, demos reference, and other go-to-market docs
- `research/` — market analysis and audience research

## Brand

All brand decisions — voice, positioning, copy, what-to-say, what-not-to-say, brand-name spelling, fonts — are settled by `brand/agency-state-brand-book.md`. Read it before writing or editing any copy or brand-adjacent doc. Visual identity (logo, typography specs, color) lives in `brand/agency-state-brand-guidelines.md`.

Don't restate brand rules in other docs. If something needs to be a rule, add it to the brand book.

## Document Conventions

- Generated markdown documents should include a YAML frontmatter header (title, date, version, status) per global preferences.
- Track versions inside files via frontmatter, not in filenames.
- New files: prefer lowercase with hyphens to match the existing `agency-state-*.md` pattern already used throughout `brand/`, `docs/`, and `research/`. Don't mix in underscores or mixed case.

## Git Discipline

- Commit in focused, descriptive units. Don't let unrelated changes pile up in one commit.
- Write commit messages that explain the *why*, not just the *what*.
- Don't commit `.DS_Store` or other macOS cruft (already in `.gitignore`).

## Website Changes

- `index.html` is hand-authored — no build step. Edit directly.
- Before claiming a visual change is done, open `index.html` in a browser and verify it renders as intended. Type-checking doesn't exist here; your eyes are the test suite.
- Keep the footer domain, nav CTA, and hero CTA in sync if any of them change.
