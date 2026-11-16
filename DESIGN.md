# ECO WARM · Design system

**Mood:** warm, calm & premium. Warm stone neutrals, deep forest green for brand and information, ember orange reserved for actions. All tokens live in [`tokens.css`](tokens.css). Components in `index.html` use only the semantic tokens below, never raw hex.

## Colour

| Role | Light | Dark | Use |
|---|---|---|---|
| `--bg` | stone-50 `#F8F5F0` | stone-950 `#151311` | page background |
| `--surface` | `#FFFFFF` | stone-850 `#1E1B18` | cards |
| `--surface-2` | stone-50 | stone-900 | fills inside cards |
| `--text` / `--text-2` / `--text-muted` | stone-900 / 700 / 500 | stone-100 / 300 / 400 | body, secondary, captions |
| `--border` / `--border-strong` | stone-200 / 300 | stone-800 / 750 | dividers, inputs |
| `--primary` | forest-600 `#23843A` | forest-400 `#5DBE70` | brand, icons, info |
| `--primary-ink` | forest-700 | forest-300 | green text |
| `--primary-soft` | forest-100 | forest-950 | tinted panels, focus ring |
| `--accent` | ember-600 `#C2490A` | ember-500 `#E8692A` | **actions only** (buttons, play) |
| `--success` / `--danger` / `--warning` | forest / clay / ochre | lighter tints | status, each with a `-soft` bg |

Rule: green says "information", orange says "press me". White text on `--accent` is 4.9:1 (WCAG AA).

## Type

- **Display:** Unbounded 600/700 (headings, numbers, logo). Its wide geometric shapes echo the poster wordmark.
- **Body:** Golos Text 400–700. Built for Cyrillic, calm and legible.
- **Scale:** 13 · 14 · 16 · 18 · 22 · 28 px, plus fluid `--t-h2`, `--t-h1`, `--t-num`.
- **Line height:** `--lh-tight` 1.1, `--lh-snug` 1.25, `--lh-body` 1.55.

## Spacing (4px base)

`--sp-1` 4 · `--sp-2` 8 · `--sp-3` 12 · `--sp-4` 16 · `--sp-5` 20 · `--sp-6` 24 · `--sp-7` 32 · `--sp-8` 40 · `--sp-9` 48 · `--sp-10` 56 · `--sp-11` 64 · `--sp-12` 80 · `--sp-13` 96

- `--gutter` (16): page side padding.
- `--section` (64): space between page sections.
- Control heights: `--h-sm` 44 · `--h-md` 48 · `--h-lg` 56. All are touch-safe (≥44px).

## Radius

`--r-sm` 8 (chips, small buttons) · `--r-md` 12 (inputs, buttons) · `--r-lg` 20 (cards, media) · `--r-pill` (pills, round buttons)

## Shadow

- `--shadow-xs`: pressed segment.
- `--shadow-sm`: cards and media.
- `--shadow-lg`: floating items (toast, play button).
- `--ring` / `--ring-danger`: focus and error rings.

All shadows are warm-tinted, and each is remapped in dark mode.

## Imagery

Every photo sits in a `.media` frame, so all images share one ratio, one radius and one colour grade.

- **Ratio.** `--ratio-photo` is 4:3 for the hero, the product frames and the result thumbs. The only exception is `--ratio-video` (9:16), because the guide clip is shot vertically.
- **Radius.** Standalone media use `--r-media` (20px). Product frames sit inside a card with 12px padding, so they use the concentric `--r-media-inset` (8px).
- **Grade.** `--media-grade` is a multiply layer: a 40% warm-stone wash, a forest glow at the top left and an ember glow at the bottom right. `--media-filter` adds a light saturate and contrast tweak. The grade is switched off (`.is-playing`) once the video player loads.
- **Files.** All local images are WebP and are made from the original sources by `make_webp.py`.

  | File | Size | Use |
  |---|---|---|
  | `hero-800.webp`, `hero-1200.webp` | 4:3 | hero, served with `srcset` |
  | `heater.webp` | 600 px wide | product photo |
  | `heater-08.webp` | 480 px wide | 0.8 kW product photo |

  The YouTube cover loads YouTube's own WebP and falls back to JPEG.
- **Loading.** The hero is eager with `fetchpriority="high"`. Every image below the fold uses `loading="lazy"` and `decoding="async"`, and has a `width`/`height` set to prevent layout shift.
- **Alt text.**
  - Content images describe the subject. Product images give the model code, power and dimensions.
  - Decorative copies use `alt=""`: the result thumbnails (the room name is next to them) and the video cover (its button has an `aria-label`).

## Backgrounds

Sections are full-width `.band` elements, and each one holds a `.wrap`. Their backgrounds alternate in this order:

| Order | Section | Class | Background |
|---|---|---|---|
| 1 | Hero + features | `.band-hero` | `--band-plain` with two brand glows, a fading grid and grain |
| 2 | Models | `.band` | `--band-plain` |
| 3 | Calculator | `.band-tint` | `--band-tint` with hairlines top and bottom |
| 4 | Video | `.band` | `--band-plain` |
| 5 | Places + contact | `.band-tint` | `--band-tint` |

The hero layers, from back to front:

1. **Glows.** Green `--glow-primary` sits at the top left and ember `--glow-accent` sits behind the photo. Both are 9–12% opacity.
2. **Grid.** `--grid-line` is drawn every `--grid-size` (48px) and fades out with an elliptical mask from the top.
3. **Grain.** `--texture-grain` is an inline SVG noise. Its strength is set by `--grain-opacity`, and it is inverted in dark mode.

These opacities are capped so the worst pixel keeps 14px green text at ≥ 4.5:1 (WCAG AA). The hero has no purple or pink gradients and no glass blur.

## Components

- **Buttons.** Every button is `.btn` plus one size and at most one variant.
  - Size: `.btn-sm` (44px, used in the header and dock), default (48px, used for result actions), or `.btn-lg` (56px, used for the hero and the calculate button).
  - Variant: `.btn-action` (orange, primary action), `.btn-ink` (dark, secondary), or `.btn-outline` (green outline).
  - All buttons share a 12px radius and semibold text.
- **Cards.** Every card is `.card`: 20px radius, a 1px border and `--shadow-sm`. The inner padding is `--card-pad`, which is 24px, or 20px at ≤ 480px. Product cards use 12px padding so their photo frame can use the concentric `--r-media-inset`.
- **Headings.** All headings use Unbounded 600.
  - `h1`: fluid size, up to 50px.
  - `.sec-title`: fluid size, up to 36px.
  - `.card-title` and product kW: 22px.
  - `.step-title`: 18px.
- **Tap targets.** Every control is at least 44 × 44px (`--h-sm`), including the delete ×, −/+, segment and text-link buttons.

## Motion

- **Durations.** `--dur-fast` .15s · `--dur` .25s · `--dur-slow` .4s · `--dur-reveal` .6s, all with `--ease`.
- **Hover.** Rules live in `@media (hover:hover) and (pointer:fine)`, so taps never leave a stuck state.
  - Buttons and product cards lift by `--lift` (2px). Buttons get `--shadow-xs` and product cards get `--shadow-md`.
  - Hover is only used on interactive elements, plus the product cards.
- **Scroll-in.**
  - JS adds `.reveal` to the section heads, the features grid, product cards, calculator columns, the video and the info cards. They fade up `--reveal-shift` (16px) as they enter the viewport.
  - Groups stagger by `--reveal-stagger` (70ms). A group arrives together as soon as any member is seen, so cards in the phone carousel are never left hidden.
  - `.reveal` is never in the HTML, so the content still shows without JS. The class is removed after the element arrives, which hands transitions back to the hover rules.
- **Reduced motion.** Under `prefers-reduced-motion` the script adds no reveals at all, and all animations and transitions are switched off.
