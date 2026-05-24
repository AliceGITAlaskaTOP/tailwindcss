---
name: tailwind
description: Use when writing, debugging, generating, refactoring, or reviewing UI code that uses Tailwind CSS (v3 or v4). Covers utility classes, responsive design, dark mode, theme variables, components, animations, gradients, container queries, custom utilities, and Tailwind Plus / UI Blocks. Trigger on HTML/JSX/Vue/Svelte/Astro files with `class=` / `className=` containing Tailwind utilities, on `.css` files using `@tailwind` / `@import "tailwindcss"` / `@theme` / `@apply` / `@utility`, or when the user asks anything about Tailwind layout/styling.
---

# Tailwind CSS Skill

You are working with Tailwind CSS — a utility-first CSS framework. Default to **v4 syntax** unless the project clearly uses v3 (check for `tailwind.config.js` and `@tailwind base/components/utilities` directives).

## Quick version detection

| Signal | Version |
|--------|---------|
| `@import "tailwindcss";` in CSS | **v4** |
| `@tailwind base; @tailwind components; @tailwind utilities;` | **v3** |
| `tailwind.config.{js,ts}` exists with `theme.extend` | likely **v3** (or v4 with `@config`) |
| `@theme { ... }` block in CSS | **v4** |
| `@tailwindcss/vite`, `@tailwindcss/postcss` packages | **v4** |
| `tailwindcss` as PostCSS plugin directly | **v3** |

When unsure, **read `package.json`** and check the `tailwindcss` version.

## How to use this skill

This skill ships with **on-demand reference files** in `reference/`. Don't read all of them — load only what the current task needs.

| Task | Read |
|------|------|
| Setting up Tailwind in a new project, fixing install issues, v3→v4 migration | `reference/01-getting-started.md` |
| State variants (hover/focus/group/peer/has/data/aria), responsive, dark mode, theme variables, colors, custom utilities, directives | `reference/02-core-concepts.md` |
| display, position, z-index, overflow, aspect-ratio, columns, float, box-sizing | `reference/03-layout.md` |
| Flexbox or Grid layouts, gap, justify/align/place | `reference/04-flexbox-grid.md` |
| padding, margin, width, height, min/max sizing, space-x/y | `reference/05-spacing-sizing.md` |
| font-size, font-weight, text-align, color, line-height, tracking, truncate, line-clamp | `reference/06-typography.md` |
| Backgrounds (incl. gradients), borders, divide, ring, outline | `reference/07-backgrounds-borders.md` |
| Shadows, opacity, blur, filters, backdrop-filter, mix-blend, masks | `reference/08-effects-filters.md` |
| Transitions, animations, transforms (scale/rotate/translate/3D), keyframes | `reference/09-transitions-transforms.md` |
| Cursors, scroll-snap, user-select, touch-action, accent-color, scroll-behavior | `reference/10-interactivity.md` |
| Tables, SVG fill/stroke, accessibility (sr-only, forced-colors) | `reference/11-tables-svg-a11y.md` |
| What Preflight resets, how to extend/disable | `reference/12-preflight.md` |
| Building a hero/pricing/navbar/modal/etc. — Tailwind Plus catalog & patterns | `reference/plus-ui-map.md` |

## Full URL map (when reference is not enough, WebFetch the docs)

Docs are at `https://tailwindcss.com/docs/<topic>`. Every sidebar entry below is a real page.

### Getting started
- `installation/using-vite`, `installation/using-postcss`, `installation/tailwind-cli`, `installation/framework-guides`, `installation/play-cdn`
- `editor-setup`, `compatibility`, `upgrade-guide`

### Core concepts
- `styling-with-utility-classes`, `hover-focus-and-other-states`, `responsive-design`, `dark-mode`, `theme`, `colors`, `adding-custom-styles`, `detecting-classes-in-source-files`, `functions-and-directives`

### Base styles
- `preflight`

### Layout
- `aspect-ratio`, `columns`, `break-after`, `break-before`, `break-inside`, `box-decoration-break`, `box-sizing`, `display`, `float`, `clear`, `isolation`, `object-fit`, `object-position`, `overflow`, `overscroll-behavior`, `position`, `top-right-bottom-left`, `visibility`, `z-index`

### Flexbox & Grid
- `flex-basis`, `flex-direction`, `flex-wrap`, `flex`, `flex-grow`, `flex-shrink`, `order`
- `grid-template-columns`, `grid-column`, `grid-template-rows`, `grid-row`, `grid-auto-flow`, `grid-auto-columns`, `grid-auto-rows`, `gap`
- `justify-content`, `justify-items`, `justify-self`, `align-content`, `align-items`, `align-self`, `place-content`, `place-items`, `place-self`

### Spacing & Sizing
- `padding`, `margin`
- `width`, `min-width`, `max-width`, `height`, `min-height`, `max-height`

### Typography (every page)
- `font-family`, `font-size`, `font-smoothing`, `font-style`, `font-weight`, `font-stretch`, `font-variant-numeric`, `font-feature-settings`
- `letter-spacing`, `line-clamp`, `line-height`
- `list-style-image`, `list-style-position`, `list-style-type`
- `text-align`, `color`, `text-decoration-line`, `text-decoration-color`, `text-decoration-style`, `text-decoration-thickness`, `text-underline-offset`
- `text-transform`, `text-overflow`, `text-wrap`, `text-indent`
- `tab-size`, `vertical-align`, `white-space`, `word-break`, `overflow-wrap`, `hyphens`, `content`

### Backgrounds
- `background-attachment`, `background-clip`, `background-color`, `background-image`, `background-origin`, `background-position`, `background-repeat`, `background-size`

### Borders
- `border-radius`, `border-width`, `border-color`, `border-style`
- `outline-width`, `outline-color`, `outline-style`, `outline-offset`

### Effects
- `box-shadow`, `text-shadow`, `opacity`, `mix-blend-mode`, `background-blend-mode`
- `mask-clip`, `mask-composite`, `mask-image`, `mask-mode`, `mask-origin`, `mask-position`, `mask-repeat`, `mask-size`, `mask-type`

### Filters
- `filter`, `blur`, `brightness`, `contrast`, `drop-shadow`, `grayscale`, `hue-rotate`, `invert`, `saturate`, `sepia`
- `backdrop-filter`, `backdrop-blur`, `backdrop-brightness`, `backdrop-contrast`, `backdrop-grayscale`, `backdrop-hue-rotate`, `backdrop-invert`, `backdrop-opacity`, `backdrop-saturate`, `backdrop-sepia`

### Tables
- `border-collapse`, `border-spacing`, `table-layout`, `caption-side`

### Transitions & Animation
- `transition-property`, `transition-behavior`, `transition-duration`, `transition-timing-function`, `transition-delay`, `animation`

### Transforms
- `backface-visibility`, `perspective`, `perspective-origin`, `rotate`, `scale`, `skew`, `transform`, `transform-origin`, `transform-style`, `translate`, `zoom`

### Interactivity
- `accent-color`, `appearance`, `caret-color`, `color-scheme`, `cursor`, `field-sizing`, `pointer-events`, `resize`
- `scroll-behavior`, `scrollbar-color`, `scrollbar-width`, `scrollbar-gutter`, `scroll-margin`, `scroll-padding`, `scroll-snap-align`, `scroll-snap-stop`, `scroll-snap-type`
- `touch-action`, `user-select`, `will-change`

### SVG
- `fill`, `stroke`, `stroke-width`

### Accessibility
- `forced-color-adjust`

## Tailwind Plus (paid) URL map

- `https://tailwindcss.com/plus/ui-blocks/application-ui` — app UI catalog
- `https://tailwindcss.com/plus/ui-blocks/marketing` — landing/marketing catalog
- `https://tailwindcss.com/plus/ui-blocks/ecommerce` — store catalog
- `https://tailwindcss.com/plus/ui-blocks/documentation/using-html` — how to use blocks
- `https://tailwindcss.com/plus/templates` — full page templates (Catalyst, Studio, Spotlight, etc.)

**License rules — must follow:**
- Plus block HTML/JSX is paid content under Tailwind Labs' EULA. **Do not** copy block source code into shared/public repositories.
- If the user is logged in to Tailwind Plus and asks for a specific block, you may `WebFetch` it from `tailwindcss.com/plus/...` and use it **within their private project**.
- Component category names and structure (in `reference/plus-ui-map.md`) are public marketing info — fine to reference.
- Instead of pasting Plus code, prefer to build equivalent components using the docs utilities; the reference files contain patterns for common UI (modal, drawer, navbar, dropdown, etc.).

## Output rules when writing Tailwind code

1. **v4 first.** If the project is v4, never emit v3-only utilities:
   - ❌ `bg-opacity-50` → ✅ `bg-black/50`
   - ❌ `flex-shrink-0` → ✅ `shrink-0`
   - ❌ `flex-grow` → ✅ `grow`
   - ❌ `!flex` → ✅ `flex!` (important goes at the END)
   - ❌ `bg-[--brand]` → ✅ `bg-(--brand)`
   - ❌ `bg-gradient-to-r` → ✅ `bg-linear-to-r`
   - ❌ `outline-none` → ✅ `outline-hidden`
   - Size renames: `shadow` → `shadow-sm`, `shadow-sm` → `shadow-xs`; same for `blur` and `rounded`; default `ring` is now 1px, use `ring-3` for old default.

2. **Mobile-first responsive.** Plain utility = base; `sm:/md:/lg:/xl:/2xl:` adds at that breakpoint and up. Never write `sm:text-center` expecting "only small" — use `text-center sm:text-left` instead.

3. **Dark mode** in v4: add `@custom-variant dark (&:where(.dark, .dark *));` to enable class-based toggling. Then use `bg-white dark:bg-gray-900`.

4. **Theme tokens via `@theme`**, not `tailwind.config.js` (in v4). Each `--<namespace>-<name>` token auto-generates utilities.

5. **Arbitrary values** with `[...]`: `w-[317px]`, `bg-[#bada55]`, `grid-cols-[200px_1fr_100px]` (underscores, not commas).

6. **No `@apply` in component-scoped CSS** (Vue/Svelte/CSS Modules) without `@reference "../path/to/app.css";` at the top — otherwise Tailwind utilities aren't available.

7. **Class ordering doesn't affect specificity** — variant specificity is equal; the last conflicting class in source order wins. Use Prettier's tailwindcss plugin if available.

## When to WebFetch vs. answer from reference

- **Reference file covers it** → answer immediately, no fetch.
- **Specific obscure utility you're unsure of** → WebFetch `https://tailwindcss.com/docs/<utility>`.
- **Plus block code request** → WebFetch the specific Plus URL (only for the user's own use, never commit to public repo).
- **Brand-new v4 feature you don't remember** → WebFetch the upgrade guide or relevant page.
