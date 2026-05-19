# Fierce Design System

Extracted from `fierce-sdr-tool/` on 2026-05-16. This document specifies only what was found in the source code — no inferred, assumed, or invented values.

---

## Table of Contents

1. [Colors](#colors)
2. [Typography](#typography)
3. [Spacing](#spacing)
4. [Gradients](#gradients)
5. [Component Patterns](#component-patterns)
6. [Layout Patterns](#layout-patterns)
7. [Motion and Transitions](#motion-and-transitions)
8. [Responsive Breakpoints](#responsive-breakpoints)
9. [Graphic Templates](#graphic-templates)

---

## Colors

### Primary Accent

| Token | Hex | Role | Files |
|-------|-----|------|-------|
| `--color-accent` | `#eb7525` | Primary brand color. Buttons, links, highlights, selected states, badges. | 8/8 |
| `--color-accent-hover` | `#d4691f` | Hover/active state for accent elements. | 5/8 |

### Gradient Palette

These colors are used together in the primary brand gradient:

| Token | Hex | Role |
|-------|-----|------|
| `--gradient-start` | `#f5a623` | Lighter orange, gradient start |
| `--gradient-mid` | `#eb7525` | Primary orange, gradient midpoint |
| `--gradient-end` | `#d45f10` | Darker orange, gradient end |

### Text Colors

| Token | Hex | Role | Files |
|-------|-----|------|-------|
| `--color-text` | `#0e0e0e` | Primary text color (near-black). Default for body and most headlines. | 6/8 |
| `--color-navy` | `#1C2B3A` | **Added 2026-05-18.** Hero headlines, large display numbers (stats), section headlines on colored backgrounds. | — |
| `--color-muted` | `#888888` | Secondary/supporting text, placeholders, labels | 6/8 |

### Background Colors

| Token | Hex | Role | Files |
|-------|-----|------|-------|
| `--color-bg` | `#ffffff` | Page background | 8/8 |
| `--color-text-inverse` | `#ffffff` | Text on dark/accent backgrounds | 8/8 |

### Surface Colors

A 3-tier surface system for visual hierarchy:

| Token | Hex | Role | Use Cases |
|-------|-----|------|-----------|
| `--surface-interactive` | `#f7f7f5` | Interactive element backgrounds | Form inputs, selectable options, scale buttons, progress tracks |
| `--surface-section` | `#F5F4F1` | Full-width section bands | Logo bar backgrounds, section dividers |
| `--surface-card` | `#FAFAF8` | Content cards within white sections | Feature cards, info cards |

### Semantic Colors

| Token | Hex | Role | Files |
|-------|-----|------|-------|
| `--color-error` | `#c73e3e` | Error states, validation messages | 5/8 |
| `--color-success` | `#16a34a` | Success states (e.g., copy confirmation) | 1/8 |

### Dark Mode / Dark Sections

| Token | Hex | Role |
|-------|-----|------|
| `--color-dark-bg` | `#0e0e0e` | Dark section backgrounds (statement sections) |
| `--color-dark-text` | `#ffffff` | Text on dark backgrounds |
| `--color-dark-muted` | `rgba(255, 255, 255, 0.5)` | Muted text on dark backgrounds |

### Border Colors

| Token | Value | Role |
|-------|-------|------|
| `--border-light` | `rgba(14, 14, 14, 0.06)` | Subtle borders (nav, footer) |
| `--border-default` | `rgba(14, 14, 14, 0.1)` | Standard borders (cards, inputs) |
| `--border-emphasis` | `rgba(14, 14, 14, 0.2)` | Emphasized borders (hover states) |

---

## Typography

### Font Families

| Token | Value | Role |
|-------|-------|------|
| `--font-serif` | `'DM Serif Display', serif` | Headlines, logos, display text, pull quotes |
| `--font-sans` | `'DM Sans', sans-serif` | Body text, buttons, labels, form inputs |

**Font Source:** Google Fonts
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,400&family=DM+Serif+Display&display=swap" rel="stylesheet">
```

### Font Weights

| Token | Value | Role |
|-------|-------|------|
| `--weight-regular` | `400` | Body text, default |
| `--weight-medium` | `500` | Labels, buttons, emphasis |
| `--weight-semibold` | `600` | Strong emphasis, headings |

### Type Scale

| Token | Size | Use Case |
|-------|------|----------|
| `--text-hero` | `clamp(48px, 8vw, 84px)` | Hero headlines |
| `--text-display` | `clamp(36px, 5vw, 52px)` | Section headlines, confirmation headlines |
| `--text-h1` | `clamp(36px, 5vw, 48px)` | Page titles, form section headlines |
| `--text-h2` | `clamp(28px, 4vw, 42px)` | Statement text, large quotes |
| `--text-h3` | `22px - 28px` | Card headings, question text |
| `--text-h4` | `20px - 24px` | Subheadings, feature labels |
| `--text-body` | `17px` | Default body text (landing pages) |
| `--text-body-small` | `15px - 16px` | Secondary body text, descriptions |
| `--text-caption` | `13px - 14px` | Labels, hints, metadata |
| `--text-micro` | `11px - 12px` | Uppercase labels, badges |

### Line Heights

| Token | Value | Use Case |
|-------|-------|----------|
| `--leading-tight` | `1.08 - 1.15` | Headlines, display text |
| `--leading-snug` | `1.3 - 1.35` | Subheadings, quotes |
| `--leading-normal` | `1.6` | Body text (default) |
| `--leading-relaxed` | `1.7` | Long-form paragraphs |

### Letter Spacing

| Token | Value | Use Case |
|-------|-------|----------|
| `--tracking-tight` | `-0.03em` | Large headlines |
| `--tracking-snug` | `-0.02em` | Headings, display text |
| `--tracking-normal` | `0` | Body text |
| `--tracking-wide` | `0.02em - 0.08em` | Labels, small caps |
| `--tracking-widest` | `0.1em - 0.15em` | Uppercase badges, section labels |

---

## Spacing

### Base Spacing Scale

Derived from values used consistently across source files:

| Token | Value | Common Uses |
|-------|-------|-------------|
| `--space-1` | `4px` | Tight gaps, micro-adjustments |
| `--space-2` | `8px` | Icon gaps, tight margins |
| `--space-3` | `12px` | Small gaps between related elements |
| `--space-4` | `16px` | Standard element spacing, input padding |
| `--space-5` | `20px` | Form group gaps, card padding |
| `--space-6` | `24px` | Section internal padding, card gaps |
| `--space-8` | `32px` | Section separations |
| `--space-10` | `40px` | Major section padding |
| `--space-12` | `48px` | Large section gaps |
| `--space-16` | `64px` | Hero/section vertical padding |
| `--space-20` | `80px` | Major section vertical padding |
| `--space-24` | `100px` | Large section padding |
| `--space-32` | `140px` | Hero sections, major spacing |

### Container Widths

| Token | Value | Use Case |
|-------|-------|----------|
| `--container-narrow` | `560px` | Confirmation pages, centered content |
| `--container-form` | `680px` | Form layouts, survey pages |
| `--container-content` | `800px` | Article/form sections |
| `--container-wide` | `1000px` | Logo grids |
| `--container-max` | `1200px` | Full-width sections, navigation |

### Border Radius

| Token | Value | Use Case |
|-------|-------|----------|
| `--radius-sm` | `4px` | Badges, small tags |
| `--radius-md` | `6px` | Buttons, small inputs |
| `--radius-lg` | `8px` | Inputs, cards |
| `--radius-xl` | `12px` | Large cards, session cards |
| `--radius-full` | `50px` | Pills, circular badges |

---

## Gradients

### Primary Brand Gradient

```css
background: linear-gradient(90deg, #f5a623, #eb7525, #d45f10);
```

**Usage:**
- Gradient text on headlines (with `-webkit-background-clip: text`)
- CTA button backgrounds
- Badge backgrounds
- Decorative accent bars
- Card top borders (2px height)

### Gradient Text Implementation

```css
.gradient-text {
    background: linear-gradient(90deg, #f5a623, #eb7525, #d45f10);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
}
```

### Dark Section Fade Gradient

Used for overlays on images in dark sections:

```css
/* Statement line fade */
background: linear-gradient(90deg, var(--color-accent), transparent);
```

---

## Component Patterns

### Navigation

**Structure:** Fixed top, logo left, CTA button right

**Specifications:**
- Height: `~68px` (padding: 20px 40px)
- Background: `--color-bg` (#ffffff)
- Border: `1px solid rgba(14, 14, 14, 0.06)`
- Shadow on scroll: `0 1px 20px rgba(0, 0, 0, 0.04)`
- z-index: `100`

**Logo:**
- Font: `--font-serif` at 24px
- Color: `--color-text`, hover: `--color-accent`
- Letter-spacing: `-0.02em`

See: `components/navigation.html`

### Buttons

#### Primary Button

- Background: `--color-accent` (#eb7525)
- Text: `#ffffff`
- Font: `--font-sans`, 15-16px, weight 500-600
- Padding: `14px 28px` (standard) or `16px 32px` (large) or `18px 40px` (hero)
- Border-radius: `6px` or `8px`
- Transition: `all 0.2s ease`

**States:**
- Hover: `--color-accent-hover` (#d4691f), `transform: translateY(-1px)`
- Active: `transform: translateY(0)`
- Disabled: `--color-muted` (#888888), `cursor: not-allowed`

See: `components/button.html`

### Form Inputs

- Font: `--font-sans`, 16px
- Padding: `16px 18px`
- Border: `2px solid rgba(14, 14, 14, 0.1)`
- Border-radius: `8px`
- Background: `--surface-interactive` (#f7f7f5)

**States:**
- Hover: `border-color: rgba(14, 14, 14, 0.2)`
- Focus: `border-color: --color-accent`, `background: #fff`, `box-shadow: 0 0 0 4px rgba(235, 117, 37, 0.08)`
- Error: `border-color: --color-error`

See: `components/form-input.html`

### Session Cards (Selectable)

- Border: `2px solid rgba(14, 14, 14, 0.1)`
- Border-radius: `12px`
- Padding: `24px`
- Background: `--color-bg`

**States:**
- Hover: `border-color: rgba(235, 117, 37, 0.4)`, `background: rgba(235, 117, 37, 0.02)`
- Selected: `border-color: --color-accent`, `background: rgba(235, 117, 37, 0.06)`

**Check indicator:**
- Size: 24px circle
- Unselected: `2px solid rgba(14, 14, 14, 0.2)`
- Selected: `--color-accent` background with white checkmark

See: `components/session-card.html`

### Feature Cards (Expect Items)

- Background: `--surface-card` (#FAFAF8)
- Padding: `32px`
- Border-radius: `12px`
- Top accent: `2px` gradient bar

**Icon:** 48x48px, stroke icons, `--color-text`

See: `components/card.html`

### Footer

- Padding: `40px`
- Border-top: `1px solid rgba(14, 14, 14, 0.06)`
- Layout: Flex, space-between
- Logo: `--font-serif`, 20px
- Copyright: 14px, `--color-muted`

See: `components/footer.html`

### Confirmation State

- Icon: 64-80px circle, `rgba(235, 117, 37, 0.1)` background, `--color-accent` stroke icon
- Headline: `--font-serif`, `--text-display`
- Message: 18px, `--color-muted` or `--color-text`

See: `components/confirmation.html`

### Stat Callout (Added 2026-05-18)

Large statistic display for key data points.

- Number: `--font-serif`, `clamp(80px, 15vw, 140px)`, gradient text or `--color-navy`
- Headline: `--font-serif`, `--text-h2`, white (dark bg) or `--color-text` (light bg)
- Subhead: 17-20px, `--color-dark-muted-light` or `--color-muted`
- Source attribution: 14px italic, `--color-dark-muted`

**Variants:**
- Dark background with gradient number
- Light background with navy number
- Inline (smaller, within content flow)

See: `components/stat-callout.html`

### Numbered List (Added 2026-05-18)

Numbered curriculum/steps with visual treatment.

- Number: `--font-serif`, 32-36px, `--color-accent` or gradient
- Text: 18px, `--color-text`
- Item separator: `1px solid rgba(14, 14, 14, 0.08)`
- Padding: `24-28px 0` per item

**Variants:**
- Stacked (curriculum style)
- Compact (badge style with circular number indicators)

See: `components/numbered-list.html`

### Pull Quote (Added 2026-05-18)

Large quote with attribution. Extends statement section.

- Quote text: `--font-serif`, `clamp(22px, 3vw, 36px)`, italic
- Decorative lines: same as statement section
- Attribution name: 16px, `--weight-semibold`
- Attribution title: 14px, `--color-dark-muted` or `--color-muted`

**Variants:**
- Dark background with decorative lines
- Light background with large quotation mark
- Inline (border-left accent)

See: `components/pull-quote.html`

### Video Phone Frame (Added 2026-05-18)

Video embed wrapped in iPhone frame for vertical video content.

- Frame: iPhone SVG asset (701.7 x 1444 viewBox)
- Screen area: 83.6% width, 85% height, positioned within frame
- Border-radius: 32px on screen
- Drop shadow: `radial-gradient(ellipse, rgba(0,0,0,0.12), transparent)`
- Play button: 72px circle, `--color-accent`, centered

**Specs:**
- Portrait orientation (9:16 aspect ratio)
- Responsive: scales proportionally, min 240px width
- Autoplay muted with controls visible, no loop

See: `components/video-phone-frame.html`

### Outcome Grid (Added 2026-05-18)

Three-column grid showing outcomes by audience level.

- Grid: `repeat(3, 1fr)`, 32px gap
- Column: `--surface-card` background, 32px padding, 12px radius
- Top accent: 3px gradient bar
- Label: `--font-serif`, 24px
- List items: 16px with checkmark icons

**Collapses to single column at 900px.**

See: `components/outcome-grid.html`

---

## Layout Patterns

### Hero Section

**Structure:**
- Full-width wrapper with optional watermark background
- Content container: `max-width: 1200px`, centered
- Padding: `180px 40px 140px` (desktop), `140px 24px 100px` (mobile)

**Elements:**
- Headline: `--font-serif`, `--text-hero`, `--tracking-tight`
- Gradient text on key phrase
- Subhead: 18-20px, `--color-text` or `--color-muted`, max-width ~580px
- Optional: Morphing word animation
- CTA button

See: `components/hero.html`

### Logo Bar

- Background: `--surface-section` (#F5F4F1)
- Padding: `80px 40px`
- Grid: 6 columns (desktop), responsive down to 2 columns
- Images: `max-width: 120px`, `filter: grayscale(100%)`, `opacity: 0.7`
- Label: 12px uppercase, `--tracking-widest`, `--color-muted`

### Statement Section (Dark)

- Background: `--color-dark-bg` (#0e0e0e)
- Padding: `100px 40px`
- Content max-width: `760px`, centered
- Text: `--font-serif`, `--text-h2`, `#ffffff`
- Decorative lines: 1px height, `--color-accent` solid + gradient fade

### Two-Column Form Layout

- Grid: `1fr 1fr` with `20px` gap
- Collapses to single column at `680px`

### Watermark Pattern

Large, semi-transparent serif text as decorative background:
- Font: `--font-serif`, `clamp(72px, 8vw, 90px)`
- Color: `#0e0e0e`, `opacity: 0.055`
- Positioned absolute, centered, `width: 200vw`
- Multiple rows with staggered margins

---

## Motion and Transitions

### Standard Transitions

| Property | Duration | Easing | Use Case |
|----------|----------|--------|----------|
| All properties | `0.2s` | `ease` | Buttons, inputs, cards |
| Opacity | `0.6s` | `ease` | Morphing text, fade effects |
| Box-shadow | `0.3s` | `ease` | Navigation shadow on scroll |
| Width (progress) | `0.5s` | `ease` | Progress bar fill |

### Transform Effects

- Button hover: `transform: translateY(-1px)`
- Button active: `transform: translateY(0)`
- Card entrance: `translateY(16px)` to `translateY(0)` with opacity

### Animations

#### Spin (Loading)
```css
@keyframes spin {
    to { transform: rotate(360deg); }
}
/* Usage: 1s linear infinite */
```

#### Smooth Scroll
```css
html {
    scroll-behavior: smooth;
}
```

---

## Responsive Breakpoints

| Breakpoint | Target |
|------------|--------|
| `1000px` | Logo grid: 6 → 4 columns |
| `900px` | Feature grid: 3 → 1 column |
| `700px` | Logo grid: 4 → 3 columns |
| `680px` | Mobile layout: reduced padding, stacked forms, centered footer |
| `500px` | Logo grid: 3 → 2 columns |

### Mobile Adjustments (≤680px)

- Nav padding: `16px 24px`
- Hero padding: `140px 24px 100px`
- Section padding: `60px-80px 24px`
- Form rows: single column
- Footer: column layout, centered

---

## Graphic Templates

These are HTML-based templates designed for image export, not web pages. They use the same visual language but with fixed dimensions and layout optimizations for social/marketing graphics.

### LinkedIn Post (1080x1080)

**File:** `examples/linkedin-post.html`

- Fixed dimensions for social export
- Dark overlay with diagonal clip-path
- Page background `#333` is specific to image export preview, not a systemic color

### Train The Trainer Graphics

**File:** `examples/ttt-graphics.html`

Contains three graphic sizes:
- LinkedIn Feed: 1200x627px
- Newsletter Banner: 600x200px
- LinkedIn Square: 1080x1080px

**Common patterns:**
- Stock image backgrounds with gradient overlays
- Gradient text headlines
- Decorative accent lines
- Logo placement

---

## File Reference

| File | Purpose |
|------|---------|
| `tokens/colors.css` | Color custom properties |
| `tokens/typography.css` | Font and type scale custom properties |
| `tokens/spacing.css` | Spacing and layout custom properties |
| `theme.css` | Consolidated theme (imports all tokens) |
| `components/*.html` | Reference implementations |
| `examples/*.html` | Source files as canonical examples |
