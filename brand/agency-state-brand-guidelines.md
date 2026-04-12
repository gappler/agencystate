# Agency State — Brand Guidelines

**URL:** agencystate.ai
**Tagline:** Do more with AI. By yourself.

---

## Logo

### Full logo (icon + wordmark + tagline)

The primary logo combines three elements: the monogram icon, the wordmark, and the tagline. These should always appear in this relationship when space allows.

### Monogram icon

- Rounded square containing lowercase "a" (bold) and "s" (regular weight)
- The weight contrast in the icon mirrors the wordmark
- Corner radius: 8px at standard size (scale proportionally)
- Use as favicon, social avatar, app icon, and anywhere the full logo won't fit

### Wordmark

- "agency" in bold (700) and "state" in regular (400), set as a single string with no space between words
- The weight shift is the visual identity — it should always be preserved
- Always lowercase

### Tagline

- "DO MORE WITH AI. BY YOURSELF." in all caps, regular weight (400), letterspaced
- Sits below the wordmark, left-aligned with the wordmark start
- Letter spacing: 3px at standard size
- Use when the tagline adds context the surrounding copy doesn't already provide (e.g., logo lockups, social bios, slide decks). Omit on pages where the headline and body copy already do the positioning work.

---

## Typography

### Primary typeface: Inter

- Source: Google Fonts — https://fonts.google.com/specimen/Inter
- License: Open Font License (free for all uses)
- Why: clean, highly legible sans-serif with excellent weight range, optimized for screens, professional without being decorative

### Weights used

| Weight | Value | Usage |
|--------|-------|-------|
| Bold | 700 | "agency" in wordmark, monogram "a", headings, emphasis |
| Regular | 400 | "state" in wordmark, monogram "s", tagline, body text, subheadings |

**Only two weights.** The entire brand system uses bold and regular. No medium, no light, no semibold. The contrast between 700 and 400 is the visual identity.

### Type scale

| Element | Size | Weight | Case | Letter spacing |
|---------|------|--------|------|----------------|
| Wordmark | 52px (reference) | 700/400 | lowercase | default |
| Tagline | 14px (reference) | 400 | uppercase | 3px |
| Monogram letters | 24px (reference) | 700/400 | lowercase | default |
| H1 headings | 36–48px | 700 | sentence case | default |
| H2 headings | 24–32px | 700 | sentence case | default |
| H3 headings | 18–24px | 400 | sentence case | default |
| Body text | 16–18px | 400 | sentence case | default |
| Labels/captions | 12–14px | 400 | uppercase | 2–3px |

All sizes are reference values at standard logo scale. Scale proportionally for different applications.

### Fallback stack

```css
font-family: 'Inter', system-ui, -apple-system, sans-serif;
```

---

## Color

### Primary palette

The brand uses a minimal, high-contrast palette. The identity lives in typography and weight contrast, not color.

| Role | Light mode | Dark mode | Usage |
|------|-----------|-----------|-------|
| Primary text | #1a1a1a | #f0f0f0 | Wordmark, icon background, headings |
| Secondary text | #6b6b6b | #a0a0a0 | Tagline, body text, captions |
| Background | #ffffff | #121212 | Page backgrounds, icon letter color |
| Accent | — | — | Reserved for future use |

### Color rules

- The logo is monochromatic. It works in any single dark color on a light background, or light color on a dark background.
- No gradients, no shadows, no glow effects on the logo.
- The monogram icon inverts: dark background with light letters in light mode, light background with dark letters in dark mode.
- If a brand accent color is introduced later, it should be used sparingly — in CTAs, links, and highlights only. The typography carries the identity, not color.

---

## Logo usage

### Minimum clear space

Maintain clear space around the full logo equal to the height of the monogram icon on all sides. No other elements should intrude into this zone.

### Minimum size

- Full logo (icon + wordmark + tagline): minimum width 280px / 2.5 inches
- Wordmark only (no icon, no tagline): minimum width 200px / 1.75 inches
- Monogram icon only: minimum 32px / 0.3 inches

### Acceptable configurations

1. **Full logo:** Icon + wordmark + tagline (primary, use whenever possible)
2. **Logo without tagline:** Icon + wordmark (for contexts where the tagline is redundant or space is tight)
3. **Wordmark only:** agencystate in bold/regular weight contrast (for inline text references, email signatures)
4. **Monogram only:** Square icon with a/s (favicon, social avatars, app icons, small format)

### Do not

- Add space between "agency" and "state" in the wordmark
- Use the wordmark in all caps or title case
- Change the weight relationship (both words same weight)
- Add color, gradient, or effects to the logo
- Rotate, skew, or distort the logo
- Place the logo on busy backgrounds without sufficient contrast
- Rearrange the elements (tagline above wordmark, icon on right, etc.)
- Use a different typeface for the wordmark

---

## Logo SVG (reference)

```svg
<svg width="100%" viewBox="0 0 680 150" xmlns="http://www.w3.org/2000/svg">
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');
.logo-heavy { font-family: 'Inter', sans-serif; font-weight: 700; font-size: 52px; fill: #1a1a1a; }
.logo-light { font-family: 'Inter', sans-serif; font-weight: 400; font-size: 52px; fill: #1a1a1a; }
.logo-tag { font-family: 'Inter', sans-serif; font-weight: 400; font-size: 14px; fill: #6b6b6b; letter-spacing: 3px; }
.mark-bg { fill: #1a1a1a; }
.mark-a { font-family: 'Inter', sans-serif; font-weight: 700; font-size: 24px; fill: #ffffff; }
.mark-s { font-family: 'Inter', sans-serif; font-weight: 400; font-size: 24px; fill: #ffffff; }
</style>
<rect class="mark-bg" x="40" y="38" width="44" height="44" rx="8"/>
<text class="mark-a" x="49" y="60" dominant-baseline="central">a</text>
<text class="mark-s" x="63" y="60" dominant-baseline="central">s</text>
<text y="75" x="100">
<tspan class="logo-heavy">agency</tspan><tspan class="logo-light">state</tspan>
</text>
<text class="logo-tag" x="100" y="105">DO MORE WITH AI. BY YOURSELF.</text>
</svg>
```

---

## Voice and tone

### Brand voice

- **Professional** — speaks with authority earned from decades of agency experience
- **Direct** — says what it means without jargon or hedge language
- **Practical** — focused on outcomes and implementation, not theory
- **Confident, not arrogant** — demonstrates capability rather than claiming it

### Writing guidelines

- Sentence case for all headings and body text (not Title Case)
- Brand name in running text is two words, title case: **Agency State**. The one-word lowercase form **agencystate** is a visual-identity convention reserved for the wordmark, logo lockups, and the domain (`agencystate.ai` / `calendly.com/agencystate`). Don't use the one-word form in prose, headlines, or body copy.
- Avoid buzzwords: "leverage," "synergy," "disrupt," "game-changer"
- Avoid hedging: "we believe," "we think," "it's possible that"
- Prefer active voice and short sentences
- When discussing AI, be specific about tools and outcomes, not abstract about "the power of AI"
