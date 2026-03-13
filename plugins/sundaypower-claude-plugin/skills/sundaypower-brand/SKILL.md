---
name: sundaypower-brand
description: Design and build websites, landing pages, and web content using the Sunday Power / Sunday OS brand identity. Use when creating NextJS components, pages, or UI that should match the Sunday Power visual style.
---

# Sunday Power Brand Design

Sunday Power is a Norwegian solar/battery energy company. The brand is bold, modern, and high-contrast — combining deep navy/purple backgrounds with electric yellow-green accents. The visual language is clean, confident, and uses generous whitespace with fluid, responsive typography.

The reference implementation is **https://insights.sundaypower.com** — use it as the design blueprint for margins, widths, weights, and spacing.

For concrete Next.js implementation patterns, component code, and CSS module examples, see `assets/nextjs.md`.

### Visual Reference

**IMPORTANT:** Before finalizing any UI work, always read the file `assets/Correct Design.png` (using the Read tool) to visually verify your output against the approved design. This image is the canonical visual reference for what correct Sunday Power design looks like. Compare your implementation against it to ensure consistent layout, spacing, color usage, and overall visual profile across all pages and components.

---

## Critical Layout & Style Rules

These are non-negotiable rules from the designer. Violating any of these is an automatic rejection:

1. **Full width or left-aligned — NEVER centered.** Content blocks, headings, text, and sections must be full-width or left-aligned. Do not center-align layouts, text blocks, or sections. Center-alignment is not part of the Sunday Power visual language.
2. **No border colors.** Do not add `border`, `border-color`, `outline`, or any visible border styling to cards, sections, containers, or components. Depth is created through background color contrast and spacing — never through borders.
3. **Always use font-weight 400 (regular). Never use 500 (medium).** Every element — headings, subtitles, body, labels, buttons, navigation — must use weight 400. The medium (500) weight exists in the font files as a fallback but must never be applied.
4. **Always use the Sunday Power logo image — never plain text.** The brand name in headers, footers, and navigation must use the actual SVG/PNG logo asset (see Assets section below), not a text element styled to look like a logo.

---

## Design Principles

1. **High contrast, bold palette** — Deep navy against electric yellow-green creates energy and confidence
2. **Warm whites** — Use `#fffff6` not pure `#fff` for a softer, warmer feel
3. **Fluid typography** — All sizing in `rem` with responsive token overrides at breakpoints
4. **Playful interactions** — Buttons pill-ify on hover; cards lift and expand corners
5. **Theme-aware via `data-theme`** — All components adapt between dark and light via CSS variables on the `<html>` element
6. **Generous spacing** — `--space-l: 9rem` for major section separation
7. **Minimal decoration** — No borders, no heavy shadows; depth via background color contrast and spacing only
8. **Consistent gaps** — `--gap` used uniformly for grids; `--pad` for component padding
9. **Semantic muting** — Use `color-mix()` for muted text and dividers — no hardcoded opacity values

---

## Visual Hierarchy

### Color Hierarchy (dark theme)

1. **Primary background** `--bg` — deep navy, the canvas
2. **Illustration/card surfaces** `--bg-illustration` — one step lighter, creates depth
3. **Hover/interactive surfaces** `--bg-card-hover` — two steps lighter, confirms interactivity
4. **Primary text** `--text` — warm white, high contrast against navy
5. **Muted text** `--text-muted` — 45% transparent, for secondary info and descriptions
6. **Dividers** `--hr` — 70% transparent, barely visible structural lines
7. **Primary accent** `--accent` — electric yellow-green, draws the eye to CTAs and key values
8. **Subtle accent** `--accent-subtle` — pale yellow, for soft highlights

### Typography Hierarchy

**All text uses weight 400.** The medium (500) weight must never be used.

| Level | Weight | Tracking | Purpose |
|---|---|---|---|
| H1 | 400 | `-0.04em` | Hero headlines — tight, commanding |
| H2 | 400 | `-0.02em` | Section headings, stat values |
| Large | 400 | — | Subtitles, card titles |
| Body | 400 | `+0.01em` | Readable paragraph text |
| Small | 400 | — | Labels, tags, metadata |

### Interaction Hierarchy

- **Buttons:** `0.3rem` radius → `50px` pill on hover (0.2s ease-in-out)
- **Cards:** `0.3rem` radius → `1rem` on hover + `translateY(-2px)` lift
- **Icon buttons:** `var(--r)` → `border-radius: 50%` on hover
- **Theme transition:** `background-color 0.4s ease` on body
- **Entrance:** fadeUp animation (opacity 0→1, translateY 1rem→0) with staggered delays

### Spacing Hierarchy

| Scale | Token | Desktop | Use |
|---|---|---|---|
| XS | `--space-xs` | `0.6rem` | Tight gaps (header padding, badge spacing) |
| S | `--space-s` | `1.5rem` | Component-level spacing (margins between elements) |
| M | `--space-m` | `2.5rem` | Section padding, hero spacing |
| L | `--space-l` | `9rem` | Major section separation |
| Pad | `--pad` | `1.5rem` | Horizontal page/component padding |
| Gap | `--gap` | `1.5rem` | Grid and component gaps |

---

## Design Tokens

The single source of truth. When building a new page, start with this foundation:

```css
:root {
  /* ── Palette ── */
  --spw-deep: #090044;
  --spw-deep7: #1a1250;
  --spw-deep14: #2b245d;
  --spw-white: #fffff6;
  --spw-white7: #f2f2e8;
  --spw-white14: #e5e5db;
  --spw-yellow-01: #faffb4;
  --spw-yellow-02: #f2ff80;
  --spw-yellow-03: #e2ff06;

  /* ── Theme tokens — dark default ── */
  --bg: var(--spw-deep);
  --bg-illustration: var(--spw-deep7);
  --bg-card-hover: var(--spw-deep14);
  --text: var(--spw-white);
  --text-muted: color-mix(in srgb, var(--text), transparent 45%);
  --hr: color-mix(in srgb, var(--text), transparent 70%);
  --btn-cta-bg: var(--spw-yellow-03);
  --btn-cta-text: var(--spw-deep);
  --btn-sec-bg: var(--spw-deep14);
  --btn-sec-text: var(--spw-yellow-02);
  --tag-bg: var(--spw-deep14);
  --tag-text: var(--spw-yellow-02);
  --accent: var(--spw-yellow-03);
  --accent-subtle: var(--spw-yellow-01);

  /* ── Typography ── */
  --font: 'Basel Grotesk', -apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif;
  --h1-size: 5.5rem;  --h1-lead: 5.5rem;  --h1-track: -0.04em;
  --h2-size: 3.3rem;  --h2-lead: 3.7rem;  --h2-track: -0.02em;
  --large-size: 1.5rem; --large-lead: 1.9rem;
  --body-size: 1rem;  --body-lead: 1.4rem; --body-track: 0.01em;
  --small-size: 0.7rem; --small-lead: 1.1rem;

  /* ── Spacing ── */
  --pad: 1.5rem;
  --gap: 1.5rem;
  --space-xs: 0.6rem;
  --space-s: 1.5rem;
  --space-m: 2.5rem;
  --space-l: 9rem;

  /* ── Radius ── */
  --r: 0.3rem;
  --r-hover: 1rem;
  --r-large: 2.5rem;

  /* ── Misc ── */
  --line: 2px;
  --transition-radius: border-radius 0.2s ease-in-out;
}

[data-theme="light"] {
  --bg: var(--spw-white);
  --bg-illustration: var(--spw-white7);
  --bg-card-hover: var(--spw-white14);
  --text: var(--spw-deep);
  --btn-sec-bg: var(--spw-white14);
  --btn-sec-text: var(--spw-deep);
  --accent: var(--spw-deep);
  --accent-subtle: var(--spw-deep7);
}

/* ── Responsive overrides ── */
@media (max-width: 991px) {
  :root {
    --pad: 1rem; --gap: 1rem; --space-l: 7rem;
    --h1-size: 4rem;    --h1-lead: 4rem;
    --h2-size: 3rem;    --h2-lead: 3.2rem;
    --large-size: 1.3rem; --large-lead: 1.7rem;
  }
}
@media (max-width: 767px) {
  :root {
    --pad: 0.5rem; --gap: 0.8rem;
    --h1-size: 2.8rem;  --h1-lead: 2.8rem;
    --h2-size: 2rem;    --h2-lead: 2.4rem;
    --large-size: 1.2rem; --large-lead: 1.5rem;
  }
}
@media (max-width: 479px) {
  :root { --h1-size: 2.2rem; --h1-lead: 2.4rem; }
}

::selection { color: #e2ff06; background: #090044; }
```

### Responsive Breakpoints

| Breakpoint | Max-width |
|---|---|
| Tablet | 991px |
| Mobile | 767px |
| Small mobile | 479px |

---

## Fonts

**Primary:** `Basel Grotesk` — weight 400 (regular) only. The 500 (medium) weight exists as a fallback but must never be used.
**Sunday OS app:** `Inter` (via `https://rsms.me/inter/inter.css`)

```css
@font-face {
  font-family: 'Basel Grotesk';
  font-weight: 400;
  font-style: normal;
  src: url('https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/fonts/Basel%20Grotesk%20Regular.woff2') format('woff2');
}
@font-face {
  font-family: 'Basel Grotesk';
  font-weight: 500;
  font-style: normal;
  src: url('https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/fonts/Basel%20Grotesk%20Medium.woff2') format('woff2');
}
```

---

## Chart & Data Visualization Colors

| Purpose | Color |
|---|---|
| Hydro / teal accent | `#2EC4B6` |
| Wind / purple | `#8B5CF6` |
| Solar / amber | `#E8A308` |
| Up-regulation / orange | `#f97316` |
| CTA yellow | `#e2ff06` |
| Blue | `#3b82f6` |
| Green (live/positive) | `#22c55e` |
| Red (error/negative) | `#ef4444` |

---

## Assets

All assets are hosted at `https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/`.

### Logos

Four color variants — each available in horizontal and vertical orientations, as compact "SPw" mark or full "Sunday Power" wordmark. Formats: SVG, PNG (2X/4X), JPG, EPS.

Base path: `Logo/{variant}/{variant} - {layout}.{ext}`

| Variant | When to use |
|---|---|
| `SPw Deep` | Default — dark navy logo for light backgrounds |
| `SPw Off White` | Light version for dark/navy backgrounds |
| `SPw Yellow` | Yellow-accent version for emphasis |
| `SPw Black` | Pure black for print or high-contrast contexts |

Layout options: `SPw Horizontal`, `SPw Vertical`, `Sunday Power Horizontal`, `Sunday Power Vertical`

Example SVG URLs:
```
https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/Logo/SPw%20Deep/SPw%20Deep%20-%20Sunday%20Power%20Horizontal.svg
https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/Logo/SPw%20Off%20White/SPw%20Off%20White%20-%20Sunday%20Power%20Horizontal.svg
https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/Logo/SPw%20Yellow/SPw%20Yellow%20-%20SPw%20Horizontal.svg
```

App icon:
```
https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/Logo/App%20icon.png
```

### Illustrations

24 SVGs using the brand palette (navy `#090044`, off-white `#fffff6`, purple `#372f75`, yellow-green `#f2ff80`). All use a consistent isometric 3D style.

Base path: `illustrations/{name}.svg`

**Buildings:** `SPw-small-building-no-solar.svg` / `SPw-small-building-solar.svg`, `SPw-tall-building-no-solar.svg` / `SPw-tall-building-solar.svg`, `SPw-wide-building-no-solar.svg` / `SPw-wide-building-solar.svg`

**Energy system:** `battery.svg`, `charge.svg`, `solar.svg`, `inverter.svg`, `grid.svg`, `ams meter.svg`, `mid meter.svg`

**Infrastructure:** `sun.svg`, `drone.svg`, `operations.svg`, `chart.svg`

**UI / app:** `computer.svg`, `door.svg`, `small house.svg`, `sundaybox.svg`

**Administrative:** `contract.svg`, `badge.svg`, `check.svg`, `enery score.svg`

### Photography

High-resolution brand photography (VSCO-treated). Base path: `Photo library/`

**Drone / aerial:** `DJI_0054-VSCO (1).jpeg`, `DJI_0101-VSCO.jpeg`, `Sunday_Power_Drone-3-VSCO.jpeg`, `Sunday_Power_Drone-4-VSCO.jpg`, `Sunday_Power_Drone-19-VSCO.jpeg`

**Properties:** `Havnegata 16-VSCO.jpeg`, `havnegata16-61-VSCO.jpeg`, `Røyken Næringspark Aug 20-VSCO.jpeg`

**Brand:** `Sunday_Power-11-VSCO.jpeg`, `Sunday_Power-12-VSCO (1).jpeg`, `Sunday_Power-16-VSCO.jpeg`, `Sunday_Power-20-VSCO (1).jpeg`, `Sunday_Power-21-VSCO 1.png`, `Sunday_Power-21-VSCO 1 2.png`, `Sunday_Power-36 (2)-VSCO 1.png`

### Team Portraits

Base path: `team/`

| File | Name | Title |
|---|---|---|
| `Jonas Ibsen Brynildsrud_CEO.jpg` | Jonas Ibsen Brynildsrud | CEO |
| `Adrian Bergem_CFO.jpg` | Adrian Bergem | CFO |
| `Einar Sunde Styreleder.jpg` | Einar Sunde | Board Chair (Styreleder) |

---

## Sunday OS App-Specific Notes

Sunday OS uses Tailwind CSS v4 with the Inter font. When building Sunday OS UI:

- Use `Inter` font (via `https://rsms.me/inter/inter.css`)
- Brand colors: `--brand-primary: #112640`, `--brand-secondary: #6fc890`, `--brand-blue-500: #2e7dcc`
- The app uses shadcn/ui-style component tokens (card, accent, border, etc.)
- Follows standard Tailwind patterns with custom brand overrides
- SPA architecture (single `<main id="app">` mount point)
