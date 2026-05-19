# Extraction Notes

This document logs inconsistencies, one-offs, ambiguities, and gaps discovered during design system extraction from `fierce-sdr-tool/`.

Extraction date: 2026-05-16

---

## Inconsistencies Found

### Error Red Variants

| Hex | Files | Decision |
|-----|-------|----------|
| `#c73e3e` | 5 files (landing pages, survey, thank-you) | **Canonical** |
| `#dc2626` | 1 file (public/index.html only) | One-off, excluded from core tokens |

**Note:** `#dc2626` appears only in the SDR Outreach Generator app. The marketing pages consistently use `#c73e3e`.

### Hover Orange Variants

| Hex | Files | Decision |
|-----|-------|----------|
| `#d4691f` | 5 files (landing pages) | **Canonical** (`--color-accent-hover`) |
| `#d16318` | 1 file (public/index.html only) | One-off, excluded from core tokens |

**Note:** `#d16318` appears only in the SDR tool as `--fierce-orange-dark`. The marketing pages use `#d4691f` as `--color-accent-hover`.

### Surface Color Variations

Three surface colors were identified with consistent semantic roles:

| Token | Hex | Files | Role |
|-------|-----|-------|------|
| `--surface-interactive` | `#f7f7f5` | 5 files | Form inputs, selectable options |
| `--surface-section` | `#F5F4F1` | 2 files | Full-width section bands |
| `--surface-card` | `#FAFAF8` | 2 files | Content cards within white sections |

**Note:** `--surface-section` and `--surface-card` currently only appear in the two main landing pages (`fierce-learning-series.html`, `fierce-learning-onsite.html`), so their canonical status is based on consistent pairing across those two files rather than 5+ file repetition.

**Recommendation:** The visual difference between the three values is subtle (~1-2 points in RGB). Confirm in future design work that they're being applied for hierarchy reasons, not by accident.

---

## App-Specific Exclusions

### SDR Tool Gray Scale (public/index.html)

The SDR Outreach Generator uses a more complex numbered gray scale that is **not part of the marketing design system**:

```css
--gray-50: #fafafa
--gray-100: #f4f4f5
--gray-200: #e4e4e7
--gray-300: #d4d4d8
--gray-400: #a1a1aa
--gray-500: #71717a
--gray-600: #52525b
--gray-700: #3f3f46
--gray-800: #27272a
--gray-900: #18181b
```

**Decision:** Excluded from core tokens. The marketing pages use semantic color names (`--color-text`, `--color-muted`) which are canonical for the design system.

### SDR Tool-Specific Tokens

These tokens appear only in `public/index.html` and are excluded from the core system:

- `--fierce-orange-light: #f5a66a` — not used in marketing pages
- `--fierce-orange-dark: #d16318` — marketing uses `#d4691f` instead

---

## Patterns Appearing Once (Potential One-Offs)

### Success Green (`#16a34a`)

- **File:** `public/index.html` only
- **Context:** Copy button success state (`.copy-btn.copied`)
- **Status:** Included in tokens as `--color-success` but flagged as low-usage. May not be needed in marketing pages.

### Tab Component

- **File:** `public/index.html` only
- **Context:** Output card tabs (Email / LinkedIn DM / Intel)
- **Status:** App-specific pattern. Not present in any marketing pages.

### Progress Bar with Shimmer Animation

- **File:** `public/index.html` only
- **Context:** CSV processing progress indicator
- **Status:** App-specific. Marketing pages have a simpler progress bar (survey page).

### File Upload Component

- **File:** `public/index.html` only
- **Context:** Dashed border upload zone with drag-and-drop
- **Status:** App-specific. Not present in marketing pages.

### Output Cards with Contact Info

- **File:** `public/index.html` only
- **Context:** Generated outreach results display
- **Status:** App-specific.

---

## Systemic Patterns

### Watermark Pattern

Present in 6 of 8 files:
- `fierce-learning-series.html`
- `fierce-learning-onsite.html`
- `fierce-pulse-survey.html`
- `fierce-pulse-thankyou.html`
- `linkedin-post.html`
- `ttt-graphics.html`

**Variations observed:**

| Property | Observed Values |
|----------|-----------------|
| Font size | `clamp(72px, 8vw, 90px)`, `80px` |
| Opacity | `0.055`, `0.12` |
| Width | `200vw`, `150%` |
| Line height | `1.15`, `1.2` |
| Gap | `0.35em`, `0.4em` |

**Recommendation:** Establish a single canonical watermark spec. Suggested defaults:
- Font: `--font-serif`, `clamp(72px, 8vw, 90px)`
- Color: `#0e0e0e`
- Opacity: `0.055` (light pages) or `0.12` (dark overlays/graphics)
- Line-height: `1.15`
- Gap: `0.35em`

Requires human confirmation before locking in.

### Primary Gradient

Highly consistent across files:
```css
linear-gradient(90deg, #f5a623, #eb7525, #d45f10)
```

Used for:
- Gradient text on headlines (6 files)
- Button backgrounds (5 files)
- Badge backgrounds (4 files)
- Decorative bars/lines (4 files)
- Card top accents (2 files)

**Status:** Canonical. No variations found.

---

## Graphic Template Notes

### linkedin-post.html

- **Page background:** `#333` — This is specific to image export preview (dark canvas for viewing the graphic). Not a systemic background color.
- **Clip-path overlay:** `polygon(0 0, 70% 0, 45% 100%, 0 100%)` — Unique to this template.

### ttt-graphics.html

- Contains three fixed-dimension graphics for social/email export
- Uses same visual patterns as landing pages (gradient text, decorative lines)
- **Page background:** `#1a1a1a` — Preview canvas only, not systemic.

**Decision:** Both files included in `examples/` and documented under "Graphic Templates" section in DESIGN_SYSTEM.md, distinct from web page patterns.

---

## Gaps Identified

### Components Not Present in Source

The following common patterns were **not found** in any source file:

| Pattern | Status |
|---------|--------|
| Testimonial/quote component | Not present |
| Pricing table | Not present |
| Accordion/FAQ | Not present |
| Modal/dialog | Not present |
| Toast/notification | Not present |
| Pagination | Not present |
| Breadcrumbs | Not present |
| Avatar/profile image | Not present |
| Tag/chip list | Not present |
| Article/blog layout | Not present |
| Pull-quote (styled blockquote) | Not present |
| Statistic callout | Not present |

**Note:** These patterns should not be invented. If needed for future pages, they should be designed and added to the system explicitly.

### Typography Gaps

- No `<blockquote>` styling defined in source
- No `<code>` or `<pre>` styling defined
- No list styling (`<ul>`, `<ol>`) beyond basic form option lists
- No table styling defined

### Missing States

- No skeleton/loading state patterns (except spinner)
- No empty state patterns (except one in SDR tool)
- No offline/error page patterns

---

## Ambiguities Requiring Confirmation

### Button Padding Variations

Multiple padding values observed:
- `14px 28px` — Navigation CTAs
- `16px 32px` — Confirmation page CTAs
- `18px 28px` — Form submit buttons
- `18px 40px` — Hero CTAs
- `18px 48px` — Survey submit

**Question:** Is this intentional hierarchy (location-based sizing) or drift? Recommend standardizing to 2-3 named sizes.

### Border Radius Variations

- `6px` — Buttons (some)
- `8px` — Inputs, buttons (some), cards (some)
- `10px` — Survey inputs
- `12px` — Session cards, feature cards

**Question:** Should inputs and buttons share the same radius? Current usage is inconsistent.

### Morphing Word Animation

Present in `fierce-learning-series.html` and `fierce-learning-onsite.html` with identical implementation (2500ms interval, 0.6s fade transition).

**Status:** Systemic pattern within landing pages. JavaScript-dependent.

---

## Additions (2026-05-18)

The following were added to the design system for the Fierce Change® landing page:

### New Token: Fierce Navy

| Token | Hex | Usage |
|-------|-----|-------|
| `--color-navy` | `#1C2B3A` | Hero headlines, large display numbers (stats), section headlines on colored backgrounds |

**Note:** This color was not in the original source files. It was added per stakeholder direction for the Fierce Change® program launch. `#0e0e0e` remains the default for body text and most headlines.

### New Components Added

| Component | File | Purpose |
|-----------|------|---------|
| Stat Callout | `components/stat-callout.html` | Large statistic display (70%, 5x) |
| Numbered List | `components/numbered-list.html` | Curriculum/step lists with visual numbers |
| Pull Quote | `components/pull-quote.html` | Quote with attribution (extends statement) |
| Video Phone Frame | `components/video-phone-frame.html` | iPhone frame around vertical video |
| Outcome Grid | `components/outcome-grid.html` | Three-column outcomes by audience |

### New Page

| Page | Location | Purpose |
|------|----------|---------|
| Fierce Change® Landing Page | `pages/fierce-change/index.html` | Program launch landing page |

**Assets included:**
- `pages/fierce-change/assets/phone-frame.svg` — iPhone frame
- `pages/fierce-change/assets/thumbnail-clark.png` — Video thumbnail

**Integrations:**
- HubSpot form: Portal ID `21395487`, Form ID `007823af-d12e-4619-8d30-89a48850d889`
- Vimeo video embed: `https://vimeo.com/1193413116`

---

## Recommendations for Future Work

1. **Standardize button sizes** — Define small/medium/large variants with consistent padding
2. **Standardize border radius** — Reduce to 3 clear tiers (sm/md/lg)
3. **Lock in watermark spec** — Choose single opacity and sizing values
4. ~~**Add pull-quote component** — Needed for article/content pages~~ ✓ Added 2026-05-18
5. ~~**Add statistic callout component** — Needed for data-driven content~~ ✓ Added 2026-05-18
6. **Define list styles** — Basic `<ul>` and `<ol>` treatments (numbered list component added, but general list styles still needed)
7. ~~**Define blockquote style** — For editorial content~~ ✓ Added via pull-quote component

---

## Source File Inventory

| File | Type | Included in Examples |
|------|------|---------------------|
| `public/index.html` | App (SDR tool) | Yes |
| `fierce-learning-series.html` | Landing page | Yes |
| `fierce-learning-onsite.html` | Landing page | Yes |
| `learning-series-thank-you.html` | Confirmation | Yes |
| `fierce-pulse-survey.html` | Survey form | Yes |
| `fierce-pulse-thankyou.html` | Confirmation | Yes |
| `linkedin-post.html` | Graphic template | Yes |
| `ttt-graphics.html` | Graphic template | Yes |
