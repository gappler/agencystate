# Project Rules — agency-state

This repo holds the Agency State website, brand system, and strategic research.

## Repo Layout

- `index.html` — single-page marketing site (agencystate.ai)
- `brand/` — brand guidelines, strategic summary, logo lockup
- `assets/` — wordmark and mark files (`.ai`, `.svg`, `.png`)
- `docs/` — pricing strategy, cohort curriculum, and other go-to-market docs
- `research/` — market analysis and audience research

## Brand Voice & Wordmark

When writing copy or docs, follow `brand/agency-state-brand-guidelines.md`. Key points:

- Brand name in running text is two words, title case: **Agency State**. The one-word lowercase form **agencystate** is reserved for visual identity — the wordmark, logo lockups, and the domain. Don't use `agencystate` in prose, headlines, or body copy.
- The repo directory is `agency-state` (kebab-case), but that's a filesystem convention, not a brand spelling. Don't propagate the hyphen into copy.
- Domain is `agencystate.ai`. Calendly handle is `calendly.com/agencystate`. These keep the one-word form because they're URLs.

## Document Conventions

- Generated markdown documents should include a YAML frontmatter header (title, date, version, status) per global preferences.
- Track versions inside files via frontmatter, not in filenames.
- New files: prefer lowercase with hyphens to match the existing `agency-state-*.md` pattern already used throughout `brand/`, `docs/`, and `research/`. Don't mix in underscores or mixed case.

## Git Discipline

- Commit in focused, descriptive units. Don't let unrelated changes pile up in one commit.
- Write commit messages that explain the *why*, not just the *what*.
- Don't commit `.DS_Store` or other macOS cruft (already in `.gitignore`).

## Typography

- Never use Space Grotesk. Inter is the only font.

## Website Changes

- `index.html` is hand-authored — no build step. Edit directly.
- Before claiming a visual change is done, open `index.html` in a browser and verify it renders as intended. Type-checking doesn't exist here; your eyes are the test suite.
- Keep the footer domain, nav CTA, and hero CTA in sync if any of them change.
