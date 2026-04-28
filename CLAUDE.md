            # Project Rules — agency-state

This is the **public** repo for the Agency State marketing site (agencystate.ai). It is served by GitHub Pages and anything committed here is publicly visible.

Internal content lives in three private companion repos: curriculum, pricing, research, and strategy in [`agency-state-curriculum`](https://github.com/gappler/agency-state-curriculum); brand resources (brand book, brand guidelines, illustrator files) in [`agency-state-practice`](https://github.com/gappler/agency-state-practice); and outbound comms in [`agency-state-publishing`](https://github.com/gappler/agency-state-publishing). If you need to read or edit brand rules, session designs, pricing strategy, or internal research, work in the appropriate private repo — not this one.

## Current state (April 2026)

Two pages are live: the homepage at `/` (umbrella personal-statement page) and `/workflow-automation-sprint/` (the current 1:1 engagement). `/associations/` is a separate coming-soon holding page, not in active development. Cohort 1 of the Annual Planning Cohort is being prepared for the week of July 13, 2026; previous cohort page work lives in `git log` history.

## Repo Layout

- `index.html` — single-page marketing site
- `assets/` — wordmark, mark, and og-image files (`.svg`, `.png`)
- `CNAME` — GitHub Pages custom domain

## Brand

Brand decisions are settled by the brand book in `agency-state-practice/brand/brand-book.md`. The visual system is settled by the brand guidelines in `agency-state-practice/brand/brand-guidelines.md`. Read both before writing or editing copy or styles on this site. Do not restate brand rules here.

## Strategy

Strategic decisions — audience, offer, format, pricing — are settled by `agency-state-curriculum/strategy/agency-state-brief-v2.md`. Read it before editing site copy related to the cohort offer.

## Document Conventions

- Generated markdown documents should include a YAML frontmatter header (title, date, version, status) per global preferences.
- Track versions inside files via frontmatter, not in filenames.
- New files: prefer lowercase with hyphens.

## Git Discipline

- **This repo is public.** Never commit internal content here. Curriculum, pricing, and research live in `agency-state-curriculum`; brand resources live in `agency-state-practice`; outbound drafts live in `agency-state-publishing`.
- Commit in focused, descriptive units. Don't let unrelated changes pile up in one commit.
- Write commit messages that explain the *why*, not just the *what*.
- Don't commit `.DS_Store` or other macOS cruft (already in `.gitignore`).

## Website Changes

- `index.html` is hand-authored — no build step. Edit directly.
- Before claiming a visual change is done, open the page in a browser and verify it renders as intended. Type-checking doesn't exist here; your eyes are the test suite.
- Keep the footer domain, nav CTA, and hero CTA in sync if any of them change.

## Deploy Workflow

The site deploys via GitHub Pages directly from `main`. The workflow is:

> **Local preview → commit → push to main → verify on the live URL.**

No staging branch. No staging environment. No preview deploy URL. No deploy gate. Local preview (`python3 -m http.server` from the repo root, or any static server) covers the iteration phase. Production-first deploys are appropriate here because the site is small, traffic is low, and `git log` covers rollback (`git revert <sha>` and push for fast rollback; the previous version is back live within a few minutes of the next Pages build).

**Do not introduce a staging branch, a staging environment, or a long-lived preview branch.** If a future change ever needs review-before-live, use a short-lived feature branch that merges straight back to `main` and deploys; do not maintain it as a separate environment.

**GitHub Pages publish latency.** Pushes take 30 seconds to a few minutes to go live. Verify on the live URL (`https://agencystate.ai/...`) — not just on local preview — before considering a deploy complete. Pages build failures are silent; if the live URL doesn't update, check the Pages settings tab in GitHub for the build status.

**OG-card cache.** Social platforms (LinkedIn, Twitter, Facebook) cache OG metadata aggressively per URL. If an OG image or metadata change ships and a stale cache is in place, force-refresh via LinkedIn Post Inspector / Twitter Card Validator.

**Plausible analytics.** Production-first means verification pageviews after a deploy go into Plausible. Local preview at `127.0.0.1` doesn't fire Plausible because the script is configured for the `agencystate.ai` domain — so the exposure is small (just whatever pageviews you generate when verifying live).
