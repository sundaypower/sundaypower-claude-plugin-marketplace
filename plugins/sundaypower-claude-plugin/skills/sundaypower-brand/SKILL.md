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
  from { opacity: 0; transform: translateY(1.2rem); }
  to   { opacity: 1; transform: translateY(0); }
}

/* Apply with staggered delays: 0.08s, 0.16s, 0.24s … 0.64s */
.fade-up {
  animation: fadeUp 0.6s ease forwards;
}
```

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
