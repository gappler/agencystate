---
title: Agency State Site — Process Log
purpose: Running record of changes to the public agency-state site repo. Append-only; new entries at the top.
date: 2026-04-27
---

# Process Log — Site

Append entries at the top. Each entry: date, what changed, why, and any notable decisions.

---

## 2026-04-27 — OG image: tagline removed; wordmark-only treatment

**What changed**

- `assets/og-image.png` — replaced. New render is wordmark-only on the cream `#FAF9F7` background; no tagline. Same 1200×630 dimensions. The old image's tagline line ("Claude Code for business and marketing.") was carried over from the previous Claude-Code-training positioning that the v1.x brand book replaced — off-brand for the current senior-marketing-leader positioning.
- `assets/og-templates/main.html` — `<div class="tagline">` element removed. `.tagline` CSS rule deleted. `body { gap: 36px }` and `flex-direction: column` removed (no longer needed with a single child); body keeps `display: flex; align-items: center; justify-content: center` to keep the wordmark centered. Other OG templates in `assets/og-templates/` (sidebar, verdana, yowie, yowie-expanded) are not affected — they're for the demo-suite OG cards, not the main site OG, and were not touched in this pass.

**Why**

The brand guidelines (v2.5) flag the official tagline ("Do more with AI on your own terms.") as written for an earlier broad-marketing-professionals positioning and queue a tagline-revisit decision. The homepage shipped on 2026-04-27 with no tagline above the bio, deferring that revisit. The OG image was still rendering an even older tagline from before the brand book's current direction, so it was actively misrepresenting the brand. Removing the tagline from the OG matches the homepage's no-tagline decision and avoids extending the older tagline into a new artifact.

This is explicitly a "remove for now" decision, not a "wordmark-only is the permanent OG treatment" decision. When the broader tagline-revisit decision lands (per the brand guidelines pending updates), the OG should be re-evaluated.

**Render workflow used (for future reference)**

The PNG was rendered from the HTML template via headless Chrome:

```
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless=new --disable-gpu --no-sandbox --hide-scrollbars \
  --window-size=1200,630 --virtual-time-budget=10000 \
  --screenshot=assets/og-image.png \
  "file://$(pwd)/assets/og-templates/main.html"
```

The `--virtual-time-budget=10000` lets Chrome wait for the Google Fonts Inter import to finish before screenshotting. Chrome rejects non-`.png` output extensions, so render straight to the final filename or a `.png` temp.

**Cache busting note**

Social platforms (LinkedIn, Twitter, Facebook) cache OG images per URL. The new image won't propagate to existing social shares automatically. If a fresh share is needed before caches expire, force-refresh via LinkedIn Post Inspector / Twitter Card Validator. The OG `<meta>` URL is unchanged (`https://agencystate.ai/assets/og-image.png`), so no cache-busting query string was added.

---

## 2026-04-27 — Deploy workflow clarified; cohort-v1-paused branch deleted; CLAUDE.md updated

**What changed**

- `CLAUDE.md` — *Current state* paragraph rewritten to reflect the new live-page set (homepage + `/workflow-automation-sprint/` engagement page; `/associations/` separately as a holding page) and to drop the holding-page line and the `cohort-v1-paused` branch reference. New *Deploy Workflow* section added after *Git Discipline* documenting the production-first workflow explicitly.
- `cohort-v1-paused` branch deleted from local and remote (`origin`). Tip commit was `6b77d4e` ("Add welcome page (post-purchase)"); reachable from `main` history via merge ancestry. `git log --all` and `git reflog` retain the commits.

**Deploy workflow now codified**

> Local preview → commit → push to main → verify on the live URL.

No staging branch, no staging environment, no preview deploys. Production-first deploys are appropriate because the site is small, traffic is low, and `git log` covers rollback. Future sessions are explicitly told not to re-introduce staging.

CLAUDE.md also names the production-first complexities so future sessions can plan around them: GitHub Pages publish latency (30s–3min, silent build failures), OG-card cache on social platforms, Plausible captures verification pageviews.

**Why**

Verification before the homepage push surfaced that the workflow had drifted toward implicit "stage in publishing repo, then ship to public repo" thinking, with the `cohort-v1-paused` branch sitting around as if it were a staged-work artifact. Neither was actually a deploy-staging environment, but the language and the dangling branch made it ambiguous. The CLAUDE.md update closes the ambiguity: the public repo deploys directly from `main`, the publishing repo's `site-copy/` is a copy-review pause (drafts, not staging), and there is no preview environment by design.

**Cross-repo ripples**

- `agency-state-publishing/CLAUDE.md` and `docs/process_log.md` updated in lockstep with this commit. The `site-copy/` line is reworded from "staging" to "drafts reviewed before applying to the public repo" — a copy-review pause, explicitly not a deploy environment.
- `agency-state-curriculum/CLAUDE.md` updated to remove the same `cohort-v1-paused` reference and to reword "stage the revised copy" → "draft the revised copy for review."

**Stale references noticed but not fixed in this pass**

- `agency-state/CLAUDE.md` (existing line, untouched in this commit) references `agency-state-curriculum/strategy/agency-state-brief-v2.md`. The current canonical brief is `agency-state-brief-v3.md`. Flagged for a separate cleanup pass.

---

## 2026-04-27 — Footer LinkedIn link rolled back from homepage and engagement page

**What changed**

- `index.html` (homepage) and `workflow-automation-sprint/index.html` (engagement page) — `<a class="footer-linkedin">LinkedIn</a>` element removed from the footer. `.footer-linkedin` and `.footer-linkedin:hover` CSS rules also removed from both files. Footers are back to the two-element pattern they had before the homepage build: wordmark left, copyright + Built with Claude Code right.
- The `Footer LinkedIn` Plausible event is no longer fired from either page.

**What stays**

- The LinkedIn link in the homepage email-contact paragraph (`#homepage-linkedin` inside `.contact-line` in Section 3) is unchanged. That's the only LinkedIn link on the site for now.

**Why**

The footer LinkedIn treatment didn't fit the footer's visual rhythm. The accent-orange uppercase link competed with the wordmark and the right-column copyright/meta block instead of integrating with them. The page draft specified the link "across all pages," but the integration question (where social links sit on the footer, whether they belong there at all, and what the visual treatment should be) is a brand-system decision that deserves its own pass — not a one-page build resolution.

The homepage copy draft is now formally out of sync with the live site on this point. The publishing-repo log notes this and explains why the draft is not being edited.

**Plausible event taxonomy after this change**

| Event name | Trigger |
|---|---|
| `Homepage offer link` | Click on the *Workflow Automation Sprint* inline link in Section 2 |
| `Homepage email` | Click on the obfuscated email link in Section 3 |
| `Homepage LinkedIn` | Click on the LinkedIn link in Section 3 |

The `Footer LinkedIn` event is no longer fired; historical data remains in Plausible.

---

## 2026-04-27 — Homepage section dividers removed; offer block collapsed to single inline-link sentence

**What changed**

- `index.html` — `border-top` removed from `.contact-section` and from `footer`. The page now has zero visible horizontal rules; whitespace alone separates sections.
- `index.html` — `.contact-section` padding bumped from `4rem 0 6rem` to `5rem 0 7rem` to give the contact block visual weight without a rule. Mobile contact-section padding kept at `3rem 0 4.5rem`.
- `index.html` — Section 2 (current offer) collapsed from a two-element block (offer paragraph + `.offer-cta-link` mini-CTA with arrow) to a single sentence:

  > "Right now the way to engage is the [Workflow Automation Sprint](/workflow-automation-sprint) — a 1:1 sprint to automate one marketing workflow over four weeks."

  The offer name is the inline accent-orange link (1px orange border-bottom prose-link styling, opacity to 0.65 on hover). No bold, no eyebrow, no separate CTA element.
- `index.html` — `.offer-cta-link` and its hover/arrow rules removed. New `.offer-prose a` rule added matching the contact-line link pattern (color, border-bottom, opacity-on-hover). `.offer-prose strong` rule removed. `.offer-section` padding tightened to `0 0 1rem` so the offer sentence reads as continuous prose with the bio above and the contact block below carries its own padding.
- `index.html` — Plausible event tracking moved from the (now-removed) `.offer-cta-link` element to the new inline `<a id="homepage-offer-link">` link. Event name kept as `Homepage offer link` (already named for the link form during the v2.4 pass).

**Why**

Two patterns from earlier passes were over-performing for the personal-statement register:

1. **Section divider rules.** Border-tops between sections felt cohort-page-y on a page where the content reads as continuous voice — bio → how to engage → how to reach me. The whole page is one extended paragraph from Greg; visible rules between thoughts fight that.
2. **Mini-CTA with arrow.** Even the lighter inline-CTA pattern (uppercase orange, no button background) pulled the eye to a "click here" element. On a personal-statement page where the bio is the lead, the offer reference should sit inside prose, not adjacent to it.

The fix on both is the same move: pull conversion-page furniture out of the personal-statement register and let the prose carry. The brand guidelines now codify both rules at v2.5.

**Brand-system change**

`brand/agency-state-brand-guidelines.md` v2.4 → v2.5 documents the rules that produced this change:
- *Layout > Section rhythm* — new exception for umbrella / personal-statement pages: no `border-top` on sections or footer.
- *Page types > Umbrella / personal statement* — *Allowed* now includes "Whitespace-only section separation"; *Not allowed* now explicitly excludes `border-top` on sections or footer, and standalone CTA buttons/arrow CTAs for offer mentions.
- *Components > Inline offer-mention pattern* — rewritten for the single-sentence form. Details in `agency-state-publishing/docs/process_log.md`.

**Plausible event taxonomy after this change**

| Event name | Trigger |
|---|---|
| `Homepage offer link` | Click on the *Workflow Automation Sprint* inline link in Section 2 |
| `Homepage email` | Click on the obfuscated email link in Section 3 |
| `Homepage LinkedIn` | Click on the LinkedIn link in Section 3 |
| `Footer LinkedIn` | Click on the LinkedIn link in the footer |

---

## 2026-04-27 — Homepage Section 2 reworked: bracket-corner card removed, replaced with inline prose offer mention; H1 "Hi." added above bio

**What changed**

- `index.html` Section 1 (bio) — new `<h1 class="bio-greeting">Hi.</h1>` added above the bio paragraph. Quiet greeting in the services-page register: `clamp(1.75rem, 3vw, 2.25rem)`, weight 300, line-height 1.1, letter-spacing −0.03em. Reveal stagger on Section 1 re-keyed: greeting `.d1`, bio paragraph `.d2`, signoff `.d3`. Hero-pattern force-visible on `DOMContentLoaded` retained.
- `index.html` Section 1 (bio) — bio paragraph dropped from lead-paragraph scale to body prose. New rule: `font-size: 1.125rem`, `line-height: 1.65`, `max-width: 60ch`. Orange `<em>` color emphasis on *That's Agency State.* removed; the bio now closes flat in primary text. CSS rules `.bio-lead em` deleted. Plain-text content updated accordingly.
- `index.html` Section 2 (current offer) — bracket-corner card replaced with prose treatment. The `<article class="offer-card">` block is gone, along with its eyebrow (`Current offer`), `<h2>` title, description paragraph, and `.button` CTA. Replaced with a single `.offer-prose` paragraph and an inline `.offer-cta-link`:

  > "The current engagement is the **Workflow Automation Sprint** — a 1:1 sprint to automate a marketing workflow that's getting in the way of your best work. Four weeks, twice-weekly sessions, using Claude and Claude Code. Your solution is the focus."
  >
  > Read the engagement details →

- `index.html` Section 2 — `.offer-section` padding reduced to `0 0 3rem` (no top padding, no border-top). The offer paragraph now reads as continuous prose from the bio rather than a card-block section break. Mobile padding `0 0 2.5rem`.
- `index.html` — CSS rules removed: `.offer-card`, `.offer-card::before`, `.offer-card::after`, `.offer-card-eyebrow`, `.offer-card-title`, `.offer-card-description`, `.button`, `.button:hover`, `.button .arrow`, `.button:hover .arrow`. The page no longer uses any button or card styles. Mobile `.button` override also removed.
- `index.html` — new CSS rules: `.offer-prose` (prose register, 60ch max-width, `text-wrap: pretty`, 1.5rem bottom margin), `.offer-prose strong` (weight 700), `.offer-cta-link` (inline CTA — 0.8125rem weight 700 uppercase 0.04em letter-spacing accent orange, no background, arrow translates 4px right on hover with 0.25s cubic-bezier easing), `.bio-greeting` (services-register H1).
- `index.html` — Plausible event renamed `Homepage offer card` → `Homepage offer link` to reflect the new link-based CTA.

**Why**

The bracket-corner card was carrying cohort/sales-page visual weight on what is fundamentally a personal-statement page. The card pattern is a strong conversion signal — bracketed corners, eyebrow, large title, button — and it pulled the homepage into a marketing register that fights the bio's "Greg explaining what he does" tone. The inline prose treatment lets the offer mention live alongside the bio as continuous prose: same accent orange, same inline-CTA type scale, no recruitment of the bracket-corner signature.

The H1 "Hi." gives the page a real top-of-document heading without becoming a hero. It's a quiet greeting that anchors the bio paragraph below it. Services-page register (light 300, smaller scale) keeps it in the personal-statement tone.

The bio-paragraph orange emphasis was removed because the user noted the phrase wasn't requested as emphasized — the brand book emphasis exception applies, but only when the conceptual payload is a deliberate page choice, not a default treatment.

**Brand-system change**

`brand/agency-state-brand-guidelines.md` v2.3 → v2.4 documents the rule that produced this change. Bracket-corner cards are now explicitly scoped to cohort / sales pages. The new *Inline offer-mention pattern* component is documented for use on umbrella / personal-statement and services / offer pages. Details in `agency-state-publishing/docs/process_log.md`.

**Plausible event taxonomy after this change**

| Event name | Trigger |
|---|---|
| `Homepage offer link` | Click on the *Read the engagement details* inline CTA link in Section 2 |
| `Homepage email` | Click on the obfuscated email link in Section 3 |
| `Homepage LinkedIn` | Click on the LinkedIn link in Section 3 |
| `Footer LinkedIn` | Click on the LinkedIn link in the footer (homepage and engagement page) |

---

## 2026-04-27 — New homepage built from copy draft v2; engagement page footer gains LinkedIn link

**What changed**

- `index.html` — the previous holding page (Coming soon eyebrow, *Build the operational systems your team has been waiting for* H1, body paragraph, holding email CTA) was replaced with the new homepage. Three sections, in order:
  1. **Bio.** Lead paragraph (Greg Appler's two-decade arc through agency, in-house, and AIA, ending in *That's Agency State.* with orange `<em>` color emphasis on the closing phrase) followed by a `— Greg Appler` signoff line in `--text-secondary`. No H1; the wordmark in the nav carries identity per the copy draft's structure note.
  2. **Current offer.** Bracket-corner card (white bg, 1px gray border, 16×16 orange L-brackets via `::before` / `::after`) containing the `Current offer` eyebrow, the `Workflow Automation Sprint` H2, the engagement description paragraph, and a `Read the engagement details` button linking to `/workflow-automation-sprint`. Card max-width 720px.
  3. **Contact.** A single line: *"If I can help you think through a workflow, answer a question, or just talk shop, email greg@agencystate.ai or find me on LinkedIn."* Email is obfuscated with the same JS string-construction pattern used on the engagement and previous holding pages; LinkedIn is a static `https://www.linkedin.com/in/gappler/` link with `target="_blank" rel="noopener"` and Plausible click tracking.
- `index.html` footer — LinkedIn link added between the wordmark and the copyright block, accent-orange uppercase pattern matching other inline CTAs. Mobile footer wraps with left-aligned content.
- `workflow-automation-sprint/index.html` footer — LinkedIn link added in the same position with the same styling. The homepage copy draft specified the footer LinkedIn should appear *across all pages, not just homepage*, so the engagement page footer was updated in the same pass. Mobile footer override (`gap: 1rem`, `.footer-right { align-items: flex-start; text-align: left }`) added to match the homepage.

**CSS additions on the homepage**

- `.bio-section` (`8.5rem 0 4rem` desktop, `6rem 0 3rem` mobile — umbrella-page hero top padding per brand guidelines)
- `.bio-lead` (`clamp(1.25rem, 1.85vw, 1.5rem)`, weight 300, line-height 1.5, letter-spacing −0.012em, max-width 56ch, `text-wrap: pretty`)
- `.bio-lead em { font-style: normal; color: var(--accent); white-space: nowrap; }` — keeps *That's Agency State.* on a single visual line at the end of the paragraph.
- `.bio-signoff` (0.9375rem, weight 300, `--text-secondary`, letter-spacing 0.02em — matches the footer-signature pattern)
- `.offer-section` (`4rem 0` desktop, `3rem 0` mobile, `border-top` per default section rhythm)
- `.offer-card` (white card with 16×16 orange L-bracket corners; `max-width: 720px`; padding `clamp(1.75rem, 3vw, 2.5rem)`)
- `.offer-card-eyebrow` (1.5rem bottom margin to title, uses `.micro` for the orange uppercase styling)
- `.offer-card-title` (`clamp(1.75rem, 3.25vw, 2.25rem)`, weight 700, line-height 1.05, letter-spacing −0.028em, max-width 18ch — matches the cohort/sales section-heading register but slightly tighter to fit inside the card)
- `.offer-card-description` (1.0625rem body register, max-width 58ch)
- `.offer-card-cta` uses the existing `.button` pattern (accent orange, uppercase 0.8125rem, 0.06em letter-spacing, arrow translates 4px on hover)
- `.contact-section` (`4rem 0 6rem` desktop, `3rem 0 4.5rem` mobile)
- `.contact-line` with inline accent-orange link styling (1px orange `border-bottom`, opacity-on-hover) — matches the `.qualifier-email a` pattern from the engagement page
- `.footer-linkedin` (0.8125rem weight 700 uppercase 0.04em letter-spacing accent orange, opacity-on-hover) — matches the inline-CTA register from the brand guidelines type scale

**Reveal-on-scroll behavior**

- Bio lead `.d1`, signoff `.d2`. Hero-pattern: forced visible on `DOMContentLoaded` (the bio-section is the umbrella-page equivalent of the hero, so it shouldn't wait for IntersectionObserver).
- Offer card and contact line use the standard observer pattern (`threshold: 0.12`, `rootMargin: '0px 0px -80px 0px'`).

**Plausible event taxonomy added in this build**

| Event name | Trigger |
|---|---|
| `Homepage offer card` | Click on the *Read the engagement details* button in Section 2 |
| `Homepage email` | Click on the obfuscated email link in Section 3 |
| `Homepage LinkedIn` | Click on the LinkedIn link in Section 3 |
| `Footer LinkedIn` | Click on the LinkedIn link in the footer (homepage and engagement page) |

The homepage `Holding page email` event from the previous holding page is no longer fired (the holding page is gone); historical data remains in Plausible.

**What didn't change**

- Brand book voice and never-say rules (no AIA paragraph reprise per the user's direction in the build session — the bio paragraph compresses the AIA decade into one clause, intentionally).
- Engagement page Section 6 contact line, qualifier, CTAs — untouched. The only change to the engagement page was the footer.
- Brand guidelines color palette, type scale, spacing scale — every value used in the homepage came from the existing tokens.

**Open items / known limitations**

- LinkedIn URL `https://www.linkedin.com/in/gappler/` is carried over from the prior homepage. If it changes, both pages and Section 3 need to update.
- The tagline question (whether the new positioning warrants a tagline above the bio) is intentionally deferred — flagged in `brand/agency-state-brand-guidelines.md` v2.3 *Pending updates*.
- Visual confirmation across desktop and mobile pending preview by Greg.

---

## 2026-04-27 — H1 emphasis removed and line-break balancing applied on Workflow Automation Sprint

**What changed**

- `workflow-automation-sprint/index.html`, hero H1: removed the `<em>terms.</em>` markup. The `.hero-headline em { font-style: normal; color: var(--accent); }` CSS rule was deleted with it. H1 now reads as plain text: *"One workflow. Four weeks. Running on your terms."*
- Added `text-wrap: balance` to the `.hero-headline` rule. Modern browsers (Chrome 114+, Edge 114+, Safari 17.5+, Firefox 121+) now balance line lengths across the headline; older browsers ignore the property and fall back to default wrapping.

**Why**

- **Emphasis:** review noted that coloring only *"terms"* orphaned the word from the conceptual phrase. *"Running on your terms"* reads as a unit; coloring just the final word breaks that unit. Trying the unemphasized version first to see if the H1 lands clean. If emphasis returns later, it should land on the full *"on your terms"* phrase, not a single word.
- **Line breaking:** the H1 was splitting *"your"* / *"terms."* across two lines, leaving a one-word last line — bad rhythm. `text-wrap: balance` lets the browser optimize line breaks across the whole headline. If balance doesn't produce clean results at some viewport, an `&nbsp;` between *"your"* and *"terms"* is the guaranteed fallback.

**No brand-system change in this entry**

The brand guidelines services-page pattern for orange `<em>` color emphasis (without underline animation) remains documented in v2.2 and available for services pages — this page is opting out, which is a per-page judgment. `text-wrap: balance` is being used here for the first time; whether it earns a brand-system default for all headings is flagged in the publishing log.

---

## 2026-04-27 — Email contact line added to Workflow Automation Sprint qualifier

**What changed**

- `workflow-automation-sprint/index.html`: new short paragraph in Section 6 between the qualifier paragraph and the final CTA button. Copy: *"Questions before scheduling? Email greg@agencystate.ai."* Email rendered as a link with id `engagement-email`.
- Reveal staggers in Section 6 re-keyed: H2 (no delay), qualifier (`d1`), email line (`d2`), button now `d3` (was `d2`).
- New `.qualifier-email` CSS rule: body-size (1.0625rem), font-weight 300, line-height 1.6, color `var(--text-secondary)`, max-width 60ch, margin-bottom 2rem. Link styling matches the homepage `.holding-cta a` pattern — `var(--accent)` color with a 1px orange `border-bottom`, opacity-on-hover transition.
- `.qualifier` margin-bottom tightened from 3rem to 1.5rem so the email line reads as an extension of the qualifier paragraph rather than a free-floating block. If the email line is removed in the future, the qualifier→button gap will need to revert to 3rem.

**Obfuscation pattern**

Matches the homepage `holding-email` pattern exactly. The mailto pattern at runtime:

- Address assembled from string parts in JavaScript (`'greg' + String.fromCharCode(64) + 'agencystate' + '.' + 'ai'`).
- `href`, `textContent`, and click handler attached via JS at script execution. Plausible event name: `'Engagement page email'`.
- Caveat preserved from homepage pattern: the `<a>` tag's static `textContent` still has *greg@agencystate.ai* in the rendered HTML before JS runs, so a raw HTML scraper still sees the address as plaintext. The obfuscation only blocks scrapers that look for `mailto:` hrefs. Decision logged separately in `agency-state-publishing/docs/process_log.md` — the strict-obfuscation question is a brand-system concern, not a per-page one.

**Why**

The page previously had only one contact path (the Calendly CTA). For prospects who want to ask a question before scheduling — typical for a senior buyer evaluating a 1:1 engagement — a low-friction email path makes sense. Pattern fidelity with the homepage matters more than tightening obfuscation on a single page.

---

## 2026-04-27 — Section padding tightened on Workflow Automation Sprint

**What changed**

- `workflow-automation-sprint/index.html`, `.section`: `padding: 4rem 0` → `padding: 3rem 0`. Applies to all five non-hero, non-final-CTA sections (value bridge, how we work together, outcomes, details — and inherited by any future sections).
- Mobile `@media (max-width: 600px)` block: removed the now-redundant `.section { padding: 3rem 0; }` override since the new desktop value matches the prior mobile value.
- `.final-cta` and `.hero` padding unchanged. Hero retains `7.5rem 0 2.5rem` desktop / `6rem 0 2rem` mobile; final CTA retains `5rem 0 6.5rem` desktop / `3.5rem 0 5rem` mobile.

**Why**

In review, the 4rem default was reading as too much air between body-end and the next H2 — adding to the long-scroll feel rather than creating useful breath. 3rem at all breakpoints reads tighter and sits better with the services-page register established in v2.1 (lighter type weights, no underline animation). The page is offer-focused, not manifesto — sections should butt up closer.

**Brand-system change (cross-repo)**

- `agency-state-publishing/brand/agency-state-brand-guidelines.md` bumped 2.1 → 2.2. Section rhythm rule now lists services pages as a third exception (alongside Hero and Final CTA) with `padding: 3rem 0` at all breakpoints. Page types > Services / offer page entry updated with the matching note. Responsive system table's *Section vertical padding* row updated to reflect the services variant at both breakpoints. Logged in `agency-state-publishing/docs/process_log.md`.

---

## 2026-04-27 — Workflow Automation Sprint hero softened to services-page register

**What changed**

- `workflow-automation-sprint/index.html`, `.hero-headline` font-weight: 700 → 300. Line-height bumped 1.02 → 1.1 to maintain readability at the lighter weight.
- `.hero-headline em`: removed `font-weight: 700`, `background-image`, `background-repeat`, `background-size`, `background-position`, `padding-bottom`. Em now carries emphasis with color alone (`color: var(--accent)`, `font-style: normal`).
- Removed `@keyframes draw-underline` rule and `.hero-headline.visible em { animation: ... }` rule. Em-underline animation gone entirely.
- `.value-heading`, `.section-heading`, `.final-cta-question`: font-weight 700 → 400. Used 400 rather than 500 to honor the brand book's *"Avoid medium and semibold — they muddy the step between light and bold"* rule.
- Inline labels in outcomes/details (`<strong>`) and CTA button text remain weight 700. Those carry the small-scale contrast the page still needs.

**Why**

Page review identified the prior treatment as performative — reading as manifesto / sales-page rather than offer-focused services. Goal: confident and quiet. Type-driven. The page should read as a senior practitioner explaining what they do, not a marketing page selling something. The em-underline draw specifically read as performing.

**Brand-system change (cross-repo)**

- `agency-state-publishing/brand/agency-state-brand-guidelines.md` bumped to v2.1. Documents the new "Services / offer page" page type and three new production type-scale variants (*Hero — services*, *Section heading — services*, *Final CTA — services*). Em-underline component pattern updated to exclude services pages explicitly. Original Hero — statement / Section heading / Final CTA headline rows are unchanged — cohort and welcome pages keep the original treatment.
- Brand-guidelines change logged separately in `agency-state-publishing/docs/process_log.md`.

---

## 2026-04-27 — Hero H1 scale reduced on Workflow Automation Sprint

**What changed**

- `workflow-automation-sprint/index.html`, `.hero-headline`: `font-size` reduced from `clamp(2.5rem, 6.5vw, 4.75rem)` to `clamp(2rem, 4.5vw, 3.5rem)`. Line-height (1.02), letter-spacing (-0.03em), weight (700), and 18ch max-width unchanged. Em-underline animation on *terms* unchanged.

**Why**

In review on a desktop viewport, the H1 was reading at ~76px (the upper clamp bound) and dominating the viewport. That scale signals manifesto / headline-driven landing page, not services page. The hero needs to read as a unified moment — H1 + subhead + CTA together — not three stacked moments where the buyer's eye lands on the H1 and has to start over for the subhead and CTA. Reference: Section AI's services hero sits at roughly 60–70% of the prior scale.

**Note on brand-range deviation**

The brand guidelines list H1 brand-range as 36–72px; new clamp floor is 32px (2rem), 4px below the documented floor. Brand ranges are described as "guardrails," not strict bounds, but flagging here so the brand guidelines may eventually want a documented "services-page hero" variant in the production type-scale table. Not blocking.

---

## 2026-04-27 — Section 2 (Trust signals) removed from Workflow Automation Sprint

**What changed**

- `workflow-automation-sprint/index.html`: Section 2 (Trust signals) removed entirely. Page now flows hero → value bridge → how we work together → outcomes → details → qualifier and final CTA. Six sections.
- Sections 3–7 renumbered to 2–6 in HTML comments and CSS section comments. No content changes to the remaining sections.
- CSS cleanup: removed `.aia-paragraph`, `.transition-paragraph`, `.pipeline-eyebrow`, `.pipeline-paragraph` (page-specific Section 2 helpers, no longer referenced) plus `.micro` and `.micro-muted` (brand-system eyebrow primitives that this page no longer uses anywhere). Both eyebrow classes remain documented in the brand guidelines and can be re-added on pages that need them.
- File size: 22,314 → 19,923 bytes after the cut.

**Why**

The Trust signals section — AIA credibility paragraph + transition paragraph + pipeline-library introduction — sat between hero and value bridge and pulled buyers away from the offer. The page's job is to qualify the buyer and book the discovery call; the founder backstory and pipeline-library framing belong elsewhere.

**Where the cut content goes**

- **AIA paragraph:** moves to the homepage in a separate pass. Not deleted from the codebase yet — the new copy lands in `agency-state-publishing/site-copy/` first when the homepage update happens.
- **Transition paragraph + pipeline-tiles paragraph:** cut entirely from this page. The pipeline-library framing is a separate piece of work; not folded into this page in any form.

**Source-of-truth update**

- The markdown copy draft `agency-state-publishing/site-copy/engagement-page-draft.md` was updated to match — Section 2 removed, remaining sections renumbered 3→2 etc., section-count line changed from *Seven sections* to *Six sections*. Logged separately in `agency-state-publishing/docs/process_log.md`.

---

## 2026-04-27 — New page: Workflow Automation Sprint

**What was added**

- New page at `/workflow-automation-sprint/` (`workflow-automation-sprint/index.html`). Single-file HTML + CSS + JS per the brand guidelines pattern. Cohort/sales page type.
- Copy source: `agency-state-publishing/site-copy/engagement-page-draft.md` (final approved draft, post-copyedit).
- Visual system: `agency-state-publishing/brand/agency-state-brand-guidelines.md` v2.0 — eight CSS variables in `:root`, Inter only, type scale per spec, spacing scale per spec.
- Section structure: hero (statement variant) → trust signals → value bridge → how we work together → outcomes → details → qualifier + final CTA. Seven sections.
- `docs/` directory created in the repo to hold this log.

**Decisions made during build**

- **Hero padding** set to the production-tightened value `7.5rem 0 2.5rem` (per the "Pending updates" note in the brand guidelines that flagged production had moved to this value on April 24). The brand guidelines doc still shows `7.5rem 0 4rem` as documented; the pending note says to update the doc once the next page lands. Once this page is reviewed and confirmed, the brand guidelines should be updated to reflect `7.5rem 0 2.5rem` as the spec.
- **Em underline target** — `terms` in *"Running on your terms."* per the build prompt.
- **Pipeline tiles section** — rendered as prose only, no placeholder cards (the library is in development). Added a small `.micro-muted` eyebrow *Pipeline library — in development* to flag status without overcommitting visually. This is consistent with the brand guidelines guidance to use a subtle treatment rather than placeholder components when content isn't ready.
- **Outcomes (Section 5)** — rendered as an `<ol>` with custom counter styling. Numbers shown as `01` / `02` / `03` / `04` in the small-uppercase orange eyebrow style (`decimal-leading-zero` counter). No new component added to the brand guidelines; this is a one-off list pattern for this page.
- **Buttons** — both CTAs render with the same `.button` styling (lifted from the cohort branch's `.book-cta` pattern). Not promoted to a guideline component; if used on a third page, document it.
- **Discovery call CTAs** — both link to `https://calendly.com/agencystate/30min` (per build instruction). Open in a new tab (`target="_blank" rel="noopener"`). Plausible custom events: `Discovery call: hero` and `Discovery call: final`.
- **Meta description** — trimmed from the subhead to 151 characters: *"A 1:1 sprint to automate a marketing workflow that's getting in the way of your best work. Four weeks, twice-weekly sessions, your solution as focus."*
- **OG image** — using the existing site default (`/assets/og-image.png`). A page-specific OG card was flagged as out-of-scope by the build prompt.
- **Plausible analytics** — included with the same script tag as the homepage and (paused) cohort page. Two custom events on the discovery-call CTAs.
- **Reveal-on-scroll** — full pattern applied per brand guidelines (`.reveal` + `.d1`–`.d5`, IntersectionObserver script with `threshold: 0.12, rootMargin: '0px 0px -80px 0px'`). Hero `.reveal` elements forced visible on `DOMContentLoaded`.

**Not done in this commit**

- Page-specific OG image. Site default in use; revisit before the page is announced publicly.
- Cross-site internal links (homepage → this page). Build prompt asked for the page to be reviewed first before any cross-site links go in.

**Verification checklist (run before announcing)**

- Desktop ≥ 920px and mobile ≤ 600px render checks.
- Em-underline animation triggers on hero load.
- Discovery-call CTAs open the Calendly URL in a new tab.
- Plausible events fire on click.
- OG/Twitter card renders at the canonical URL.
