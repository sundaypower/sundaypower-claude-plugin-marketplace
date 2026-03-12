---
name: sundaypower-brand
description: Design and build websites, landing pages, and web content using the Sunday Power / Sunday OS brand identity. Use when creating NextJS components, pages, or UI that should match the Sunday Power visual style.
---

# Sunday Power Brand Design

Sunday Power is a Norwegian solar/battery energy company. The brand is bold, modern, and high-contrast — combining deep navy/purple backgrounds with electric yellow-green accents. The visual language is clean, confident, and uses generous whitespace with fluid, responsive typography.

The reference implementation is **https://insights.sundaypower.com** — use it as the design blueprint for margins, widths, weights, and spacing.

---

## Color Palette

### Core Swatches

| Token | Hex | Usage |
|---|---|---|
| `--spw-deep` | `#090044` | Primary dark background, text on light theme |
| `--spw-deep7` | `#1a1250` | Illustration/card backgrounds (dark theme) |
| `--spw-deep14` | `#2b245d` | Card hover, secondary button backgrounds (dark theme) |
| `--spw-white` | `#fffff6` | Primary light background, text on dark theme (warm white) |
| `--spw-white7` | `#f2f2e8` | Illustration backgrounds (light theme) |
| `--spw-white14` | `#e5e5db` | Secondary button backgrounds (light theme) |
| `--spw-yellow-01` | `#faffb4` | Lightest yellow accent, subtle accent (light theme) |
| `--spw-yellow-02` | `#f2ff80` | Medium yellow accent, secondary/tag button text (dark theme) |
| `--spw-yellow-03` | `#e2ff06` | Primary CTA yellow, text selection highlight, stats values |

### Theme Tokens

Use these semantic tokens in components — never hardcode raw hex values:

#### Dark Theme — Default

```css
[data-theme="dark"], :root {
  --bg: #090044;
  --bg-illustration: #1a1250;
  --bg-card-hover: #2b245d;
  --text: #fffff6;
  --text-muted: color-mix(in srgb, var(--text), transparent 45%);
  --hr: color-mix(in srgb, var(--text), transparent 70%);
  --btn-cta-bg: #e2ff06;
  --btn-cta-text: #090044;
  --btn-sec-bg: #2b245d;
  --btn-sec-text: #f2ff80;
  --tag-bg: #2b245d;
  --tag-text: #f2ff80;
  --accent: #e2ff06;
  --accent-subtle: #faffb4;
}
```

#### Light Theme

```css
[data-theme="light"] {
  --bg: #fffff6;
  --bg-illustration: #f2f2e8;
  --bg-card-hover: #e5e5db;
  --text: #090044;
  --text-muted: color-mix(in srgb, var(--text), transparent 45%);
  --hr: color-mix(in srgb, var(--text), transparent 70%);
  --btn-cta-bg: #e2ff06;
  --btn-cta-text: #090044;
  --btn-sec-bg: #e5e5db;
  --btn-sec-text: #090044;
  --tag-bg: #2b245d;
  --tag-text: #f2ff80;
  --accent: #090044;
  --accent-subtle: #1a1250;
}
```

> Theme is switched via `data-theme="light"` attribute on `<html>` or a parent element — not via CSS class.

### Selection Styling

```css
::selection {
  color: #e2ff06;
  background: #090044;
}
```

---

## Typography

### Font Family

- **Primary:** `Basel Grotesk` — weights 400 (regular) and 500 (medium)
- **Fallback:** `-apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif`
- **Sunday OS app:** `Inter` (loaded from `https://rsms.me/inter/inter.css`)

Font files are self-hosted from the design tokens repo:

```css
@font-face {
  font-family: 'Basel Grotesk';
  font-weight: 400;
  src: url('https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/fonts/Basel%20Grotesk%20Regular.woff2') format('woff2');
}
@font-face {
  font-family: 'Basel Grotesk';
  font-weight: 500;
  src: url('https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/fonts/Basel%20Grotesk%20Medium.woff2') format('woff2');
}

--font: 'Basel Grotesk', -apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif;
```

### Font Smoothing

Always apply:

```css
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

### Type Scale Tokens

```css
:root {
  --h1-size: 5.5rem;
  --h1-lead: 5.5rem;
  --h1-track: -0.04em;

  --h2-size: 3.3rem;
  --h2-lead: 3.7rem;
  --h2-track: -0.02em;

  --large-size: 1.5rem;
  --large-lead: 1.9rem;

  --body-size: 1rem;
  --body-lead: 1.4rem;
  --body-track: 0.01em;

  --small-size: 0.7rem;
  --small-lead: 1.1rem;
}
```

### Type Scale Reference

| Level | Size | Line Height | Letter Spacing | Weight |
|---|---|---|---|---|
| H1 | 5.5rem | 5.5rem | `-0.04em` | 500 |
| H2 | 3.3rem | 3.7rem | `-0.02em` | 500 |
| Large | 1.5rem | 1.9rem | — | 400 |
| Body | 1rem | 1.4rem | `0.01em` | 400 |
| Small | 0.7rem | 1.1rem | — | 400/500 |
| Stats/ticker | uses H2 tokens | | | 500 |

> Note: letter-spacing uses **`em`** units, not `rem`.

### Responsive Typography

```css
/* Tablet — max-width: 991px */
--h1-size: 4rem;    --h1-lead: 4rem;
--h2-size: 3rem;    --h2-lead: 3.2rem;
--large-size: 1.3rem; --large-lead: 1.7rem;

/* Mobile — max-width: 767px */
--h1-size: 2.8rem;  --h1-lead: 2.8rem;
--h2-size: 2rem;    --h2-lead: 2.4rem;
--large-size: 1.2rem; --large-lead: 1.5rem;

/* Small mobile — max-width: 479px */
--h1-size: 2.2rem;  --h1-lead: 2.4rem;
```

---

## Spacing System

### Spacing Tokens

```css
:root {
  --pad: 1.5rem;      /* horizontal page/component padding */
  --gap: 1.5rem;      /* grid and component gaps */
  --space-xs: 0.6rem;
  --space-s: 1.5rem;
  --space-m: 2.5rem;
  --space-l: 9rem;    /* large vertical section spacing */
}

/* Tablet — max-width: 991px */
--pad: 1rem;
--gap: 1rem;
--space-l: 7rem;

/* Mobile — max-width: 767px */
--pad: 0.5rem;
--gap: 0.8rem;
```

### Specific Spacing Values

| Context | Value |
|---|---|
| Body padding | `4rem` top / `1.5rem` horizontal / `1rem` bottom |
| Header padding | `0.6rem` vertical / `1.5rem` horizontal |
| Hero section | `4rem` top / `2.5rem` bottom |
| Card padding | `1.5rem` |
| Button padding | `0.6rem` vertical / `2rem` horizontal |
| Stats section padding | `2.5rem` vertical |
| Stat item padding-left | `1.5rem` |
| Footer padding | `2.5rem` top / `1.5rem` bottom |
| Hero h1 margin-bottom | `1.5rem` |
| Card title margin-bottom | `0.4rem` |
| Card description margin-bottom | `1.5rem` |

---

## Border Radius

### Radius Tokens

```css
:root {
  --r: 0.3rem;       /* default — buttons, cards, badges */
  --r-hover: 1rem;   /* interactive hover state for cards */
  --r-large: 2.5rem; /* prominent elements */
}
```

| State | Value |
|---|---|
| Default (buttons, cards) | `0.3rem` |
| Card hover | `1rem` |
| Button hover | `50px` (full pill) |
| Large cards/sections | `2.5rem` |
| Badge | `0.25rem` |

---

## Layout

### Container & Grid

```css
--line: 2px;   /* border/divider line width */

/* 2-column card grid */
grid-template-columns: 1fr 1fr;
gap: var(--gap); /* 1.5rem */

/* 3-column stats grid */
grid-template-columns: 1fr 1fr 1fr;
gap: var(--gap);

/* Hero text max-widths */
hero: max-width 52rem;
hero subtitle: max-width 36rem;

/* Card */
min-height: 28rem; /* desktop */
min-height: 24rem; /* tablet */
```

### Responsive Breakpoints

| Breakpoint | Max-width |
|---|---|
| Tablet | 991px |
| Mobile | 767px |
| Small mobile | 479px |

### Responsive Layout Changes

- **Mobile (767px):** Card grid → 1-column; stats grid → 1-column
- **Tablet (991px):** Card height reduces to 24rem; stats stay 3-column

---

## Components

### Buttons

**Primary CTA:**
```css
.btn {
  display: inline-block;
  padding: 0.6rem 2rem;
  border-radius: var(--r); /* 0.3rem */
  background-color: var(--btn-cta-bg);  /* #e2ff06 */
  color: var(--btn-cta-text);           /* #090044 */
  letter-spacing: 0.01em;
  font-weight: 500;
  transition: var(--transition-radius), background-color 0.3s ease;
}
.btn:hover {
  border-radius: 50px; /* pill shape */
}
```

**Secondary:**
```css
.btn.secondary {
  background-color: var(--btn-sec-bg);   /* #2b245d dark / #e5e5db light */
  color: var(--btn-sec-text);            /* #f2ff80 dark / #090044 light */
}
```

**Tag:**
```css
.tag {
  background-color: var(--tag-bg);   /* #2b245d */
  color: var(--tag-text);            /* #f2ff80 */
  font-size: var(--small-size);      /* 0.7rem */
  font-weight: 500;
  padding: 0.35rem 1.2rem;
  border-radius: var(--r);
}
```

**Badge (e.g. "beta"):**
```css
.badge {
  font-size: 0.55rem;
  font-weight: 500;
  line-height: 1;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  padding: 0.2em 0.5em;
  border-radius: 0.25rem;
}
```

### Key Interaction Patterns

```css
:root {
  --transition-radius: border-radius 0.2s ease-in-out;
}
```

- **Buttons:** `0.3rem` → `50px` pill on hover (`0.2s ease-in-out`)
- **Cards:** `0.3rem` → `1rem` on hover + `translateY(-2px)` lift
- **Theme toggle:** `background-color 0.4s ease` on body

### Cards

```css
.card {
  background: var(--bg-illustration);   /* #1a1250 dark */
  border-radius: var(--r);              /* 0.3rem */
  padding: var(--pad);                  /* 1.5rem */
  min-height: 28rem;
  transition: var(--transition-radius), transform 0.3s ease;
}
.card:hover {
  border-radius: var(--r-hover);        /* 1rem */
  background: var(--bg-card-hover);    /* #2b245d dark */
  transform: translateY(-2px);
}
```

### Navigation

- Fixed top header, `z-index: 1000`
- `backdrop-filter: blur(20px)`
- Padding: `0.6rem` vertical / `1.5rem` horizontal
- Background: `var(--bg)` with blur

### Stats / Ticker

- Font: H2 size/lead/track tokens
- Color: `var(--accent)` — `#e2ff06` on dark, `#090044` on light
- Stat item: `padding-left: 1.5rem`, `border-left: var(--line) solid var(--hr)` (2px)

### Dividers / Lines

```css
hr, .divider {
  border-color: var(--hr); /* color-mix(in srgb, var(--text), transparent 70%) */
  border-width: 1px;
}
.stat-border {
  border-left: var(--line) solid var(--hr); /* 2px */
}
```

### Animations

```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(1rem); }
  to   { opacity: 1; transform: translateY(0); }
}

/* Helper class — apply directly to elements */
.animate-in { opacity: 0; animation: fadeUp 0.5s ease forwards; }

/* Staggered delay utilities */
.delay-1 { animation-delay: 0.05s; } .delay-2 { animation-delay: 0.1s; }
.delay-3 { animation-delay: 0.15s; } .delay-4 { animation-delay: 0.2s; }
.delay-5 { animation-delay: 0.3s; } .delay-6 { animation-delay: 0.35s; }
.delay-7 { animation-delay: 0.4s; }
```

---

## Insights / Dashboard Components

Patterns from `shared.css` used in data/dashboard pages.

**Header** — fixed, `z-index: 1000`, `backdrop-filter: blur(20px)`, `0.6rem var(--pad)` padding, bg uses `color-mix(in srgb, var(--bg), transparent 20%)`. Icon buttons (theme toggle, lang toggle): `2.4rem` square, `var(--r)` default, hover → `border-radius: 50%`.

**Auth dropdown** — avatar button `2.4rem` circle; dropdown `.open` class; positioned `top: calc(100% + 0.4rem)` right-aligned; uses `var(--bg-illustration)` bg with `box-shadow: 0 4px 16px rgba(0,0,0,0.25)`.

**Breadcrumb** — `padding-top: 3rem`; links use `var(--text-muted)`, `.current` uses `var(--text) font-weight: 500`.

**Page title** — `max-width: 48rem`; h1 uses H2 tokens at `font-weight: 400`; subtitle uses `var(--text-muted)`.

**Controls** — flex wrap, `gap: 0.8rem`. Selects: `appearance: none`, `var(--bg-illustration)` bg, chevron via `::after` pseudo. Toggle groups: flex row, overflow hidden, `.active` → `var(--btn-cta-bg)`. Period pills: hover/active → `var(--r-hover)`, active color → `var(--tag-text)`.

**Status banner** — small dot (`6px` circle) + text. States: `.live` `#22c55e`, `.mock`/`.loading` `var(--spw-yellow-03)`, `.error` `#ef4444`. Loading pulses via `@keyframes pulse`.

**Chart container** — `var(--bg-illustration)` bg, `var(--r)` radius, `var(--gap)` padding. Inner `.chart-wrap` has `height: 480px`. `.loading-overlay` covers inset-0 with a progress bar (`var(--spw-yellow-03)` fill, width animated via JS).

**Summary grid** — `repeat(4, 1fr)` → 2-col at 991px → 1-col at 479px. Cards: `var(--bg-illustration)`, hover → `var(--r-hover)`. Value uses `var(--large-size)`, label uses `var(--small-size) + var(--text-muted)`. Colored dot (`8px`) for source indicator.

**Explainer** — `<details>` with custom chevron `::before` (CSS border trick, rotates 45deg when `[open]`). Max-width `48rem`.

**Save / Share / Viewer** — `.btn-save` is full-width secondary button. `.viewer-banner` shows avatar + name in `var(--bg-illustration)` strip. `.share-toast` is a flex row with URL input + copy button (CTA style), animated with `fadeUp`.

**Saved analyses grid** — `auto-fill minmax(300px, 1fr)`. Cards hover to `var(--bg-card-hover)`. Type badge uses CTA colors. Delete button absolute top-right, hover → `#ef4444`. Verified badge: `color-mix(in srgb, #22c55e, transparent 80%)` bg.

**Footer** — `var(--hr)` divider line, flex space-between. Mobile → column. Logo SVG at `opacity: 0.5`.

**Badge** — `0.55rem`, uppercase, `0.06em` tracking, `vertical-align: super`, CTA colors.

---

## Design Principles

1. **High contrast, bold palette** — Deep navy against electric yellow-green creates energy and confidence
2. **Warm whites** — Use `#fffff6` not pure `#fff` for a softer, warmer feel
3. **Fluid typography** — All sizing in `rem` with responsive token overrides at breakpoints
4. **Playful interactions** — Buttons pill-ify on hover; cards lift and expand corners
5. **Theme-aware via `data-theme`** — All components adapt between dark and light via CSS variables on the element
6. **Generous spacing** — `--space-l: 9rem` for major section separation
7. **Minimal decoration** — No heavy shadows; depth via color contrast and spacing
8. **Consistent gaps** — `--gap` used uniformly for grids; `--pad` for component padding
9. **Semantic muting** — Use `--text-muted` (45% transparent) for secondary text; `--hr` (70% transparent) for dividers

---

## Full CSS Variable Template

When building a new page, start with this foundation:

```css
:root {
  /* Palette */
  --spw-deep: #090044;
  --spw-deep7: #1a1250;
  --spw-deep14: #2b245d;
  --spw-white: #fffff6;
  --spw-white7: #f2f2e8;
  --spw-white14: #e5e5db;
  --spw-yellow-01: #faffb4;
  --spw-yellow-02: #f2ff80;
  --spw-yellow-03: #e2ff06;

  /* Theme tokens — dark default */
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

  /* Typography */
  --font: 'Basel Grotesk', -apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif;
  --h1-size: 5.5rem;  --h1-lead: 5.5rem;  --h1-track: -0.04em;
  --h2-size: 3.3rem;  --h2-lead: 3.7rem;  --h2-track: -0.02em;
  --large-size: 1.5rem; --large-lead: 1.9rem;
  --body-size: 1rem;  --body-lead: 1.4rem; --body-track: 0.01em;
  --small-size: 0.7rem; --small-lead: 1.1rem;

  /* Spacing */
  --pad: 1.5rem;
  --gap: 1.5rem;
  --space-xs: 0.6rem;
  --space-s: 1.5rem;
  --space-m: 2.5rem;
  --space-l: 9rem;

  /* Radius */
  --r: 0.3rem;
  --r-hover: 1rem;
  --r-large: 2.5rem;

  /* Misc */
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

/* Tablet */
@media (max-width: 991px) {
  :root {
    --pad: 1rem;
    --gap: 1rem;
    --space-l: 7rem;
    --h1-size: 4rem;    --h1-lead: 4rem;
    --h2-size: 3rem;    --h2-lead: 3.2rem;
    --large-size: 1.3rem; --large-lead: 1.7rem;
  }
}

/* Mobile */
@media (max-width: 767px) {
  :root {
    --pad: 0.5rem;
    --gap: 0.8rem;
    --h1-size: 2.8rem;  --h1-lead: 2.8rem;
    --h2-size: 2rem;    --h2-lead: 2.4rem;
    --large-size: 1.2rem; --large-lead: 1.5rem;
  }
}

/* Small mobile */
@media (max-width: 479px) {
  :root {
    --h1-size: 2.2rem;  --h1-lead: 2.4rem;
  }
}

::selection {
  color: #e2ff06;
  background: #090044;
}

body {
  font-family: var(--font);
  font-size: var(--body-size);
  line-height: var(--body-lead);
  letter-spacing: var(--body-track);
  background: var(--bg);
  color: var(--text);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  transition: background-color 0.4s ease, color 0.4s ease;
}
```

---

## Assets

All assets are hosted at `https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/`.

### Fonts

Self-host Basel Grotesk directly from the repo:

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

### Logos

Four color variants — each available in horizontal and vertical orientations, as compact "SPw" mark or full "Sunday Power" wordmark. Formats: SVG, PNG (2X/4X), JPG, EPS.

Base path: `Logo/{variant}/{variant} - {layout}.{ext}`

| Variant | When to use |
|---|---|
| `SPw Deep` | Default — dark navy logo for light backgrounds |
| `SPw Off White` | Light version for dark/navy backgrounds |
| `SPw Yellow` | Yellow-accent version for emphasis |
| `SPw Black` | Pure black for print or high-contrast contexts |

Layout options per variant:
- `SPw Horizontal` — compact "SPw" wordmark, horizontal
- `SPw Vertical` — compact "SPw" wordmark, stacked
- `Sunday Power Horizontal` — full name, horizontal
- `Sunday Power Vertical` — full name, stacked

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

**Buildings:**
- `SPw-small-building-no-solar.svg` / `SPw-small-building-solar.svg`
- `SPw-tall-building-no-solar.svg` / `SPw-tall-building-solar.svg`
- `SPw-wide-building-no-solar.svg` / `SPw-wide-building-solar.svg`

**Energy system components:**
- `battery.svg` — energy storage
- `charge.svg` — charging system
- `solar.svg` — solar panel
- `inverter.svg` — power inverter
- `grid.svg` — network grid (isometric)
- `ams meter.svg` — advanced metering system
- `mid meter.svg` — meter display

**Infrastructure & data:**
- `sun.svg` — stylized sun with radiating rays
- `drone.svg` — property survey drone
- `operations.svg` — monitoring dashboard
- `chart.svg` — data visualization

**UI / application:**
- `computer.svg`
- `door.svg`
- `small house.svg`
- `sundaybox.svg` — Sunday Power branded device

**Administrative:**
- `contract.svg`
- `badge.svg`
- `check.svg`
- `enery score.svg` — energy scoring metric

Example usage:
```html
<img src="https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/illustrations/battery.svg" alt="Battery storage" />
```

### Photography

High-resolution brand photography (VSCO-treated). Base path: `Photo library/`

**Drone / aerial:**
- `DJI_0054-VSCO (1).jpeg`
- `DJI_0101-VSCO.jpeg`
- `Sunday_Power_Drone-3-VSCO.jpeg`
- `Sunday_Power_Drone-4-VSCO.jpg`
- `Sunday_Power_Drone-19-VSCO.jpeg`

**Properties / locations:**
- `Havnegata 16-VSCO.jpeg`
- `havnegata16-61-VSCO.jpeg`
- `Røyken Næringspark Aug 20-VSCO.jpeg`

**Brand photography:**
- `Sunday_Power-11-VSCO.jpeg`
- `Sunday_Power-12-VSCO (1).jpeg`
- `Sunday_Power-16-VSCO.jpeg`
- `Sunday_Power-20-VSCO (1).jpeg`
- `Sunday_Power-21-VSCO 1.png`
- `Sunday_Power-21-VSCO 1 2.png`
- `Sunday_Power-36 (2)-VSCO 1.png`

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

---

## Quick Reference: What Makes It "Sunday Power"

- Deep navy `#090044` backgrounds
- Electric yellow-green `#e2ff06` CTAs and accent values
- Warm white `#fffff6` (not pure white)
- Basel Grotesk font — weights 400 and 500
- Buttons pill-ify on hover (`50px` radius)
- Cards lift (`translateY(-2px)`) and round corners to `1rem` on hover
- Negative letter-spacing on headings (`-0.04em` H1, `-0.02em` H2)
- Positive letter-spacing on body (`0.01em`)
- `data-theme` attribute for theme switching
- `--pad` / `--gap` as the core spacing primitives
- `color-mix()` for muted text and divider lines — no hardcoded opacity values
- FadeUp entrance animations with staggered delays

---

## Next.js Internal Platform Patterns

Reference implementation: `/Users/alexanderrydfjord/code/internal-vibe-platform`

**Stack:** Next.js 15 App Router · React 19 · TypeScript · NextAuth v5 · CSS Modules · Tailwind v4 (minimal use)

---

### Project Structure

```
src/
├── app/
│   ├── layout.tsx                  # Root layout — <html data-theme="dark">
│   ├── page.tsx                    # Redirects to /dashboard
│   ├── login/
│   │   ├── page.tsx                # Google OAuth login page
│   │   └── login.module.css
│   ├── dashboard/
│   │   ├── page.tsx                # Protected landing page (hero + cards + stats + footer)
│   │   └── dashboard.module.css
│   └── api/auth/[...nextauth]/
│       └── route.ts                # NextAuth handler
├── components/
│   ├── Header.tsx                  # Server component — logo + UserMenu + ThemeToggle
│   ├── header.module.css
│   ├── ThemeToggle.tsx             # Client component — theme toggle button
│   ├── themeToggle.module.css
│   ├── UserMenu.tsx                # Client component — avatar dropdown + sign out
│   └── userMenu.module.css
├── lib/
│   └── auth.ts                     # NextAuth config (Google, @sundaypower.no domain)
└── styles/
    └── globals.css                 # Brand tokens + base styles
```

---

### globals.css — Body Rule

The body uses fixed pixel values (matching insights.sundaypower.com), not CSS token references:

```css
body {
  font-family: var(--font);
  font-size: 18px;
  line-height: 24px;
  letter-spacing: var(--body-track);
  background: var(--bg);
  color: var(--text);
  padding: 4rem var(--pad) 1rem;  /* 4rem top = header offset */
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  transition: background-color 0.4s ease, color 0.4s ease;
}

/* Global h1 class for hero headings */
.heroH1 {
  font-size: var(--h1-size);
  line-height: var(--h1-lead);
  letter-spacing: var(--h1-track);
  font-weight: 400;
  margin-bottom: var(--space-s);
}
```

---

### Header Component (Server)

`src/components/Header.tsx` — server component, reads session, passes `signOutSlot` as ReactNode to client UserMenu.

```tsx
import Link from "next/link";
import { auth, signOut } from "@/lib/auth";
import UserMenu from "./UserMenu";
import ThemeToggle from "./ThemeToggle";
import styles from "./header.module.css";

export default async function Header() {
  const session = await auth();

  const signOutAction = (
    <form action={async () => { "use server"; await signOut({ redirectTo: "/login" }); }}>
      <button type="submit" className="signOutBtn">Sign out</button>
    </form>
  );

  return (
    <header className={styles.header}>
      <Link href="/dashboard" className={styles.logo}>
        <svg className={styles.logoSvg} viewBox="0 0 1247 199" xmlns="http://www.w3.org/2000/svg" aria-label="Sunday Power">
          {/* Full Sunday Power wordmark SVG paths — fill="currentColor" adapts to theme */}
          <path d="M91.4427 66.2507L48.728 56.282C36.7015 53.3744 30.6882 47.767 30.6882 39.4597..." />
          {/* ... remaining paths */}
        </svg>
        <span className={styles.logoDivider}>/ Internal</span>
      </Link>
      <div className={styles.headerRight}>
        {session?.user && <UserMenu user={session.user} signOutSlot={signOutAction} />}
        <ThemeToggle />
      </div>
    </header>
  );
}
```

**header.module.css:**
```css
.header {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  padding: 0.6rem var(--pad);
  display: flex; justify-content: space-between; align-items: center;
  background-color: color-mix(in srgb, var(--bg), transparent 20%);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
}
.headerRight { display: flex; align-items: center; gap: 0.5rem; }
.logo { display: flex; align-items: center; gap: 0.5rem; text-decoration: none; color: var(--text); }
.logoSvg { height: 1.05rem; width: auto; display: block; fill: currentColor; flex-shrink: 0; }
.logoDivider { color: var(--text-muted); font-weight: 400; font-size: 1rem; letter-spacing: 0.01em; }
```

**Key pattern:** The Sunday Power wordmark SVG uses `fill: currentColor` — it automatically adapts to dark/light theme without any extra CSS.

**Full logo SVG paths** (viewBox="0 0 1247 199", fill="currentColor"):
```
M91.4427 66.2507L48.728 56.282C36.7015 53.3744 30.6882 47.767 30.6882 39.4597C30.6882 33.3642 33.6223 28.4525 39.5008 24.7142C45.3792 20.9759 52.9476 19.1068 62.2059 19.1068C81.5623 19.1068 92.0648 28.4525 93.7236 47.1439L119.85 42.7826C118.606 29.9063 112.976 19.5533 102.951 11.7341C92.9253 3.91481 79.2814 0 61.9986 0C51.0814 0 41.398 1.69261 32.9691 5.08822C24.5402 8.48384 17.9671 13.3228 13.2706 19.626C8.57405 25.9292 6.22059 33.1565 6.22059 41.3288C6.22059 49.9165 8.67773 57.2477 13.5816 63.3432C18.4855 69.4387 25.6392 73.5923 35.0427 75.8041L80.2456 86.6036C91.9922 89.3762 97.8706 95.534 97.8706 105.087C97.8706 112.429 94.8329 118.203 88.7471 122.429C82.6613 126.655 74.3672 128.763 63.8647 128.763C39.9466 128.763 26.9559 116.853 24.8824 93.0418L0 97.1954C2.35346 113.26 8.8125 125.721 19.3875 134.578C29.9625 143.446 44.301 147.87 62.4133 147.87C74.025 147.87 84.3616 146.074 93.4125 142.47C102.464 138.867 109.555 133.675 114.666 126.894C119.777 120.113 122.338 112.221 122.338 103.218C122.338 93.6648 119.643 85.7002 114.252 79.3347C108.86 72.9693 101.25 68.6079 91.4427 66.2507Z
M200.292 99.2724C200.292 107.995 198.146 115.056 193.864 120.456C189.582 125.856 183.839 128.556 176.654 128.556C171.397 128.556 167.25 127.029 164.213 123.987C161.175 120.944 159.651 116.79 159.651 111.526V42.7827H134.769V113.81C134.769 124.059 137.879 132.294 144.099 138.524C150.32 144.755 158.479 147.87 168.567 147.87C175.337 147.87 181.599 146.385 187.333 143.405C193.066 140.425 197.389 136.375 200.292 131.255H200.707V145.378H225.174V42.7827H200.292V99.2724Z
M300.029 40.2905C293.249 40.2905 286.997 41.7755 281.264 44.7557C275.53 47.736 271.207 51.7858 268.304 56.9051H267.89V42.7827H243.422V145.378H268.304V88.8883C268.304 80.1656 270.45 73.1044 274.732 67.7046C279.014 62.3049 284.758 59.605 291.942 59.605C297.199 59.605 301.346 61.1315 304.384 64.174C307.421 67.2166 308.945 71.3702 308.945 76.635V145.378H333.828V74.3505C333.828 64.1013 330.717 55.8667 324.497 49.6362C318.276 43.4058 310.117 40.2905 300.029 40.2905Z
M422.99 56.6973H422.575C419.673 51.713 415.391 47.7358 409.72 44.7556C404.048 41.7753 397.755 40.2904 390.85 40.2904C382.422 40.2904 374.812 42.5022 368.042 46.9363C361.272 51.3703 355.943 57.6631 352.075 65.8354C348.208 74.0077 346.27 83.4157 346.27 94.0802C346.27 104.745 348.208 114.153 352.075 122.325C355.943 130.497 361.272 136.79 368.042 141.224C374.812 145.658 382.422 147.87 390.85 147.87C397.9 147.87 404.297 146.385 410.031 143.405C415.764 140.425 420.087 136.447 422.99 131.463H423.405V145.378H447.873V2.49219H422.99V56.6973ZM416.562 119.314C411.586 125.617 405.085 128.763 397.071 128.763C389.057 128.763 382.898 125.679 378.202 119.521C373.505 113.364 371.152 104.88 371.152 94.0802C371.152 83.2807 373.505 74.7969 378.202 68.6391C382.898 62.4813 389.192 59.3972 397.071 59.3972C404.95 59.3972 411.586 62.5436 416.562 68.8468C421.539 75.1499 424.027 83.5611 424.027 94.0802C424.027 104.599 421.539 113.01 416.562 119.314Z
M537.035 56.6975H536.62C533.717 51.7131 529.436 47.736 523.764 44.7557C518.093 41.7755 511.8 40.2905 504.895 40.2905C496.466 40.2905 488.857 42.5023 482.087 46.9364C475.316 51.3704 469.987 57.6632 466.12 65.8355C462.253 74.0078 460.314 83.4158 460.314 94.0803C460.314 104.745 462.253 114.153 466.12 122.325C469.987 130.497 475.316 136.79 482.087 141.224C488.857 145.658 496.466 147.87 504.895 147.87C511.945 147.87 518.342 146.385 524.076 143.405C529.809 140.425 534.132 136.448 537.035 131.463H537.45V145.378H561.917V42.7827H537.035V56.6975ZM530.607 119.314C525.631 125.617 519.13 128.763 511.116 128.763C503.102 128.763 496.943 125.679 492.247 119.521C487.55 113.364 485.197 104.88 485.197 94.0803C485.197 83.2808 487.55 74.797 492.247 68.6392C496.943 62.4814 503.237 59.3973 511.116 59.3973C518.995 59.3973 525.631 62.5437 530.607 68.8469C535.584 75.1501 538.072 83.5612 538.072 94.0803C538.072 104.599 535.584 113.011 530.607 119.314Z
M613.962 114.433C610.779 120.664 607.876 126.967 605.253 133.332H604.839C604.973 130.84 605.046 124.61 605.046 114.641V42.7827H580.578V126.894C580.578 132.844 582.133 137.413 585.244 140.601C588.354 143.789 592.885 145.378 598.825 145.378L569.796 198.545H595.922L678.656 42.7827H652.115L613.962 114.433Z
M779.108 13.707C771.156 6.23047 760.55 2.49219 747.279 2.49219H681.134V145.378H706.016V84.7345H747.279C760.55 84.7345 771.156 80.9962 779.108 73.5196C787.06 66.0431 791.031 56.0743 791.031 43.6133C791.031 31.1524 787.06 21.1836 779.108 13.707ZM760.654 58.6703C756.994 62.4813 751.976 64.3816 745.621 64.3816H706.016V22.8451H745.621C751.976 22.8451 756.994 24.7454 760.654 28.5564C764.313 32.3673 766.149 37.3829 766.149 43.6133C766.149 49.8438 764.313 54.8593 760.654 58.6703Z
M867.44 46.8325C859.903 42.4712 851.028 40.2905 840.796 40.2905C830.563 40.2905 821.688 42.4712 814.151 46.8325C806.613 51.1939 800.808 57.4555 796.733 65.6278C792.659 73.8001 790.616 83.2808 790.616 94.0803C790.616 104.88 792.659 114.371 796.733 122.533C800.808 130.705 806.613 136.967 814.151 141.328C821.688 145.689 830.563 147.87 840.796 147.87C851.028 147.87 859.903 145.689 867.44 141.328C874.978 136.967 880.784 130.705 884.858 122.533C888.933 114.361 890.975 104.88 890.975 94.0803C890.975 83.2808 888.933 73.8001 884.858 65.6278C880.784 57.4555 874.978 51.1939 867.44 46.8325ZM859.457 119.625C855.03 125.721 848.81 128.763 840.796 128.763C832.781 128.763 826.561 125.721 822.134 119.625C817.707 113.53 815.499 105.015 815.499 94.0803C815.499 83.1458 817.707 74.6308 822.134 68.5354C826.561 62.4399 832.781 59.3973 840.796 59.3973C848.81 59.3973 855.03 62.4399 859.457 68.5354C863.884 74.6308 866.093 83.1458 866.093 94.0803C866.093 105.015 863.884 113.53 859.457 119.625Z
M1057.69 42.7827L1020.16 113.395C1017.25 119.075 1014.76 125.233 1012.69 131.879H1012.28C1012.69 126.198 1012.9 120.944 1012.9 116.095V61.4741C1012.9 55.3787 1011.3 50.7473 1008.13 47.5594C1004.95 44.3715 1000.32 42.7827 994.237 42.7827H972.465L934.934 113.395C932.311 118.514 929.822 124.682 927.469 131.879H927.054C927.469 126.063 927.676 120.799 927.676 116.095V42.7827H903.416V126.686C903.416 132.637 905.044 137.247 908.289 140.497C911.534 143.748 916.137 145.378 922.078 145.378H943.02L980.344 74.9735C982.832 70.2695 985.663 64.039 988.845 56.2821H989.26C988.845 62.9279 988.638 68.1927 988.638 72.066V126.686C988.638 132.637 990.266 137.247 993.511 140.497C996.756 143.748 1001.36 145.378 1007.3 145.378H1028.24L1082.78 42.7827H1057.69Z
M1153.28 47.0402C1146.09 42.5439 1137.65 40.2905 1127.98 40.2905C1118.31 40.2905 1109.66 42.5439 1102.06 47.0402C1094.46 51.5365 1088.51 57.8709 1084.23 66.0432C1079.95 74.2155 1077.8 83.5612 1077.8 94.0803C1077.8 104.599 1079.87 114.329 1084.02 122.429C1088.17 130.529 1094.01 136.79 1101.54 141.224C1109.08 145.658 1117.89 147.87 1127.98 147.87C1140.01 147.87 1150.2 144.828 1158.56 138.732C1166.93 132.637 1172.28 124.475 1174.63 114.226L1152.03 110.487C1150.65 116.302 1147.78 120.871 1143.43 124.194C1139.07 127.517 1133.79 129.179 1127.57 129.179C1118.99 129.179 1112.33 126.095 1107.56 119.937C1103.63 114.869 1101.35 108.099 1100.65 99.6877H1175.67V94.0803C1175.67 83.4158 1173.73 74.0389 1169.87 65.9393C1166 57.8397 1160.46 51.5365 1153.28 47.0402ZM1101.4 82.6578C1102.53 76.8011 1104.61 71.9517 1107.66 68.12C1112.5 62.0245 1119.34 58.982 1128.19 58.982C1135.24 58.982 1140.87 61.0588 1145.09 65.2124C1149.31 69.3661 1151.62 75.1812 1152.03 82.6578H1101.4Z
M1243.06 40.2905C1236.14 40.2905 1230 41.9831 1224.61 45.3788C1219.21 48.7744 1215.35 53.9249 1212.99 60.8511H1212.58V42.7827H1188.11V145.378H1212.99V89.9267C1212.99 81.4844 1215.45 74.9112 1220.35 70.1968C1225.26 65.4928 1232.14 63.1356 1240.99 63.1356H1247V40.2905H1243.06Z
```

---

### ThemeToggle Component (Client)

`src/components/ThemeToggle.tsx` — deferred mount prevents hydration flash. Reads/writes `spw-theme` in localStorage (same key as insights.sundaypower.com).

```tsx
"use client";
import { useEffect, useState } from "react";

type Theme = "dark" | "light";

export default function ThemeToggle() {
  const [theme, setTheme] = useState<Theme>("dark");
  const [mounted, setMounted] = useState(false);

  useEffect(() => {
    const stored = localStorage.getItem("spw-theme") as Theme | null;
    const current = stored ?? (document.documentElement.getAttribute("data-theme") as Theme) ?? "dark";
    setTheme(current);
    document.documentElement.setAttribute("data-theme", current);
    setMounted(true);
  }, []);

  function toggle() {
    const next: Theme = theme === "dark" ? "light" : "dark";
    setTheme(next);
    document.documentElement.setAttribute("data-theme", next);
    localStorage.setItem("spw-theme", next);
  }

  // Render moon icon as static placeholder before mount (avoids hydration mismatch)
  if (!mounted) return <button className={styles.toggle} aria-label="Toggle theme" type="button">🌙</button>;

  return (
    <button className={styles.toggle} onClick={toggle} type="button">
      {theme === "dark" ? <MoonIcon /> : <SunIcon />}
    </button>
  );
}
```

**themeToggle.module.css:**
```css
.toggle {
  width: 2.4rem; height: 2.4rem; border-radius: var(--r); border: none;
  background: var(--bg-illustration); color: var(--text); cursor: pointer;
  display: flex; align-items: center; justify-content: center;
  transition: border-radius 0.2s ease-in-out, background-color 0.3s ease;
}
.toggle:hover { border-radius: 50%; background: var(--bg-card-hover); }
.icon { width: 1.1rem; height: 1.1rem; transition: transform 0.3s ease; }
.toggle:hover .icon { transform: rotate(15deg); }
```

---

### UserMenu Component (Client)

`src/components/UserMenu.tsx` — receives user data and `signOutSlot` (a server action form) as props. This is the key pattern for mixing server actions with client interactivity.

```tsx
"use client";
import { useEffect, useRef, useState } from "react";

interface UserMenuProps {
  user: { name?: string | null; email?: string | null; image?: string | null; };
  signOutSlot: React.ReactNode;  // Server action form passed from server parent
}

export default function UserMenu({ user, signOutSlot }: UserMenuProps) {
  const [open, setOpen] = useState(false);
  const ref = useRef<HTMLDivElement>(null);

  useEffect(() => {
    function handleClick(e: MouseEvent) {
      if (ref.current && !ref.current.contains(e.target as Node)) setOpen(false);
    }
    document.addEventListener("click", handleClick);
    return () => document.removeEventListener("click", handleClick);
  }, []);

  return (
    <div ref={ref} style={{ position: "relative" }}>
      <button onClick={() => setOpen(v => !v)} aria-expanded={open}>
        {user.image ? <img src={user.image} referrerPolicy="no-referrer" /> : initials}
      </button>
      {open && (
        <div className={styles.dropdown}>
          <div className={styles.name}>{user.name ?? user.email}</div>
          {signOutSlot}
        </div>
      )}
    </div>
  );
}
```

**Sign out button styling** — target the global class applied to the server-rendered form button:
```css
.dropdown :global(.signOutBtn) {
  font-size: var(--small-size); font-weight: 500;
  background: none; border: none; color: var(--text); cursor: pointer; padding: 0;
  transition: color 0.2s ease;
}
.dropdown :global(.signOutBtn):hover { color: var(--btn-cta-bg); }
```

---

### Dashboard Page Layout

`src/app/dashboard/page.tsx` — server component with auth guard. Page sections match insights.sundaypower.com exactly.

```tsx
import { auth } from "@/lib/auth";
import { redirect } from "next/navigation";
import Header from "@/components/Header";
import styles from "./dashboard.module.css";

export default async function DashboardPage() {
  const session = await auth();
  if (!session) redirect("/login");

  return (
    <>
      <Header />

      <section className={styles.hero}>
        <div className={`${styles.heroTag} animate-in delay-1`}>Internal Platform</div>
        <h1 className="heroH1 animate-in delay-2">
          Internal<br />Sales <span className={styles.accent}>Platform</span>
        </h1>
        <p className={`${styles.heroSub} animate-in delay-3`}>...</p>
      </section>

      <section className={`${styles.cardGrid} animate-in delay-4`}>
        <div className={`${styles.card} animate-in delay-4`}>
          <div className={styles.cardIcon}><svg viewBox="0 0 200 160" fill="none">...</svg></div>
          <div className={styles.cardContent}>
            <div className={styles.cardTitle}>Module Name</div>
            <p className={styles.cardDesc}>Description</p>
            <span className={styles.btnCta}>Coming soon</span>
          </div>
        </div>
      </section>

      <div className={`${styles.hr} animate-in delay-7`} />

      <section className={`${styles.stats} animate-in delay-7`}>
        <div className={styles.statItem}>
          <div className={styles.statValue}>4</div>
          <div className={styles.statLabel}>Modules in development</div>
        </div>
      </section>

      <footer className={styles.footer}>
        <div className={styles.footerLeft}>
          <span className={styles.footerText}>Sunday Power © 2025</span>
        </div>
        <div className={styles.footerLinks}>
          <a href="mailto:info@sundaypower.no">Feedback</a>
          <a href="https://sundaypower.com">sundaypower.com</a>
        </div>
      </footer>
    </>
  );
}
```

**dashboard.module.css key rules:**
```css
/* Hero */
.hero { padding-top: 4rem; padding-bottom: var(--space-m); max-width: 52rem; }
.heroTag { display: inline-block; font-size: var(--small-size); font-weight: 500; color: var(--tag-text); background: var(--tag-bg); padding: 0.35rem 1.2rem; border-radius: var(--r); margin-bottom: var(--space-s); }
.accent { color: var(--spw-yellow-03); }
[data-theme="light"] .accent { color: var(--spw-deep); }
.heroSub { font-size: var(--large-size); line-height: var(--large-lead); color: var(--text-muted); max-width: 36rem; }

/* Card grid */
.cardGrid { display: grid; grid-template-columns: 1fr 1fr; gap: var(--gap); margin-bottom: var(--space-l); }
.card {
  background: var(--bg-illustration); border-radius: var(--r); padding: var(--gap);
  display: flex; flex-direction: column; justify-content: space-between; min-height: 28rem;
  transition: var(--transition-radius), transform 0.3s ease;
  position: relative; overflow: hidden; color: var(--text); cursor: pointer;
}
.card::before {
  content: ''; position: absolute; inset: 0; border-radius: inherit;
  background: linear-gradient(180deg, transparent 40%, color-mix(in srgb, var(--bg), transparent 40%) 100%);
  opacity: 0; transition: opacity 0.4s ease; pointer-events: none;
}
.card:hover { border-radius: var(--r-hover); transform: translateY(-2px); }
.card:hover::before { opacity: 1; }
.cardIcon { width: 100%; flex: 1; display: flex; align-items: center; justify-content: center; padding: var(--space-m) 0; position: relative; z-index: 1; }
.cardIcon svg { width: 100%; max-width: 14rem; height: auto; opacity: 0.9; transition: transform 0.4s ease, opacity 0.3s ease; }
.card:hover .cardIcon svg { transform: scale(1.04); opacity: 1; }
.cardTitle { font-size: var(--large-size); line-height: var(--large-lead); font-weight: 500; margin-bottom: 0.4rem; }
.cardDesc { font-size: var(--body-size); color: var(--text-muted); margin-bottom: var(--space-s); }
.btnCta { display: inline-block; padding: 0.6rem 2rem; border-radius: var(--r); background: var(--btn-cta-bg); color: var(--btn-cta-text); transition: var(--transition-radius); }
.btnCta:hover { border-radius: 50px; }

/* Stats */
.stats { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: var(--gap); padding: var(--space-m) 0; }
.statItem { padding-left: var(--gap); border-left: 2px solid var(--hr); }
.statValue { font-size: var(--h2-size); line-height: var(--h2-lead); letter-spacing: var(--h2-track); font-weight: 400; color: var(--spw-yellow-03); }
[data-theme="light"] .statValue { color: var(--spw-deep); }
.statLabel { font-size: var(--small-size); color: var(--text-muted); font-weight: 500; margin-top: 0.2rem; }

/* Footer */
.footer { padding: var(--space-m) 0 var(--space-s); display: flex; justify-content: space-between; align-items: center; border-top: 1px solid var(--hr); }
.footerText, .footerLinks a { font-size: var(--small-size); color: var(--text-muted); text-decoration: none; }
.footerLinks { display: flex; gap: var(--gap); }
.footerLinks a:hover { color: var(--text); }

/* Responsive */
@media (max-width: 991px) { .card { min-height: 24rem; } }
@media (max-width: 767px) {
  .cardGrid { grid-template-columns: 1fr; }
  .card { min-height: 20rem; }
  .stats { grid-template-columns: 1fr; gap: var(--space-s); }
  .footer { flex-direction: column; align-items: flex-start; gap: var(--space-s); }
}
```

---

### Card SVG Illustration Pattern

All card illustrations use `viewBox="0 0 200 160" fill="none"`. Use brand colors directly (not `currentColor`) for chart elements, and `currentColor` for neutral grid lines/labels.

```tsx
<svg viewBox="0 0 200 160" fill="none">
  {/* Grid lines — use currentColor at low opacity */}
  <line x1="20" y1="130" x2="180" y2="130" stroke="currentColor" strokeWidth="0.5" opacity="0.15"/>

  {/* Data elements — use brand colors */}
  <rect x="30" y="85" width="20" height="45" rx="2" fill="#8B5CF6" opacity="0.6"/>
  <rect x="114" y="45" width="20" height="85" rx="2" fill="#e2ff06" opacity="0.7"/>
  <polyline points="40,85 68,72 96,58" stroke="#2EC4B6" strokeWidth="2" fill="none"/>

  {/* Legend */}
  <circle cx="20" cy="20" r="3" fill="#8B5CF6"/>
  <text x="27" y="22.5" fill="currentColor" fontSize="6.5" fontFamily="sans-serif" opacity="0.55">Label</text>
</svg>
```

**Chart color palette for illustrations:**
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

### Login Page

`src/app/login/page.tsx` — centered card layout, Google OAuth via NextAuth server action.

```tsx
import { signIn } from "@/lib/auth";

export default function LoginPage() {
  return (
    <div className={styles.page}>        {/* min-height: 100vh, flex center */}
      <div className={styles.card}>      {/* bg-illustration, border-radius: var(--r-large) = 2.5rem */}
        <div className={styles.logoWrap}>
          <img src="https://raw.githubusercontent.com/sundaypower/claude-design-tokens/main/Logo/SPw%20Off%20White/SPw%20Off%20White%20-%20Sunday%20Power%20Horizontal.svg" />
          <p className={styles.subtitle}>Internal Sales Platform</p>
        </div>
        <form action={async () => { "use server"; await signIn("google", { redirectTo: "/dashboard" }); }}>
          <button type="submit" className={styles.signInButton}>
            {/* Google SVG icon */}
            Sign in with Google
          </button>
        </form>
        <p className={styles.footer}>Only @sundaypower.no accounts are allowed</p>
      </div>
    </div>
  );
}
```

---

### Auth Configuration

`src/lib/auth.ts` — NextAuth v5, Google provider, domain-restricted to `@sundaypower.no`.

```ts
import NextAuth from "next-auth";
import Google from "next-auth/providers/google";

const ALLOWED_DOMAIN = process.env.ALLOWED_DOMAIN ?? "sundaypower.no";

export const { handlers, auth, signIn, signOut } = NextAuth({
  providers: [
    Google({
      clientId: process.env.GOOGLE_CLIENT_ID,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET,
      authorization: { params: { hd: ALLOWED_DOMAIN } },
    }),
  ],
  callbacks: {
    signIn({ account, profile }) {
      if (account?.provider === "google") {
        return (profile?.email ?? "").endsWith(`@${ALLOWED_DOMAIN}`);
      }
      return false;
    },
    session({ session }) { return session; },
  },
  session: { strategy: "jwt" },
  pages: { signIn: "/login", error: "/login" },
});
```

**Required env vars:**
```
NEXTAUTH_SECRET=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
ALLOWED_DOMAIN=sundaypower.no
```

**Auth guard pattern** (use in every protected page/layout):
```tsx
const session = await auth();
if (!session) redirect("/login");
```

---

### Next.js-Specific Notes

- **`data-theme`** is set on `<html>` in `app/layout.tsx` as default `"dark"`. ThemeToggle updates it client-side.
- **No `SessionProvider`** needed — auth uses server-side `auth()` calls throughout. `signOut` uses server actions.
- **CSS Modules** for all component styles. Global utility classes (`animate-in`, `delay-*`, `heroH1`) in `globals.css`.
- **Tailwind v4** is installed but largely unused — all styling is CSS Modules + CSS variables.
- **`@import "tailwindcss"`** must be first line of `globals.css` for Tailwind v4.
- **Header is NOT in root layout** — only added to dashboard pages. Login has its own full-screen layout.
- **`localStorage` key** for theme: `spw-theme` (matches insights.sundaypower.com).
