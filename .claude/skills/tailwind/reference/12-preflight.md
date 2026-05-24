# Preflight (Tailwind's base styles)

Auto-injected into the `base` layer when you `@import "tailwindcss"`. Built on **modern-normalize**.

## What it resets

1. **All margins removed** — `<h1>`, `<p>`, `<blockquote>`, `<ul>`, `<figure>`, etc. all start with `margin: 0`.
2. **Borders reset to `0 solid currentColor`** — so `border` adds a reliable 1px line without needing color or style.
3. **Headings (`h1`–`h6`) unstyled** — `font-size: inherit; font-weight: inherit`. Force you to opt in via utilities (`text-2xl font-bold`).
4. **Lists unstyled** — `<ul>` and `<ol>` get `list-style: none; padding: 0`. To restore bullets either add `list-disc list-inside` or use `prose` from `@tailwindcss/typography`.
5. **Images/video/SVG are block-level and constrained** — `display: block; max-width: 100%; height: auto`.
6. **Buttons are reset** — no default background or border; cursor is `pointer` only when `<button>` is `not disabled`.
7. **Inputs inherit color and font** — easier to style with utilities.
8. **`hidden` attribute respected** — `[hidden]` always gets `display: none`.

## Extend Preflight

Add element-level rules to the base layer:

```css
@layer base {
  h1 { font-size: var(--text-3xl); font-weight: 700; }
  h2 { font-size: var(--text-2xl); font-weight: 600; }
  a  { color: var(--color-blue-600); text-decoration: underline; }
  img { display: inline; }      /* opt-out of block default for inline icons */
}
```

## Disable Preflight (keep theme + utilities only)

```css
/* Don't use `@import "tailwindcss"` */
@import "tailwindcss/theme.css" layer(theme);
@import "tailwindcss/utilities.css" layer(utilities);
```

You'll get the theme variables and utility classes, but no element resets.

## Disable specific Preflight rules
There's no built-in selector toggle. To override a Preflight rule, write a more-specific rule in `@layer base`:

```css
@layer base {
  /* Restore default list bullets globally */
  ul { list-style: disc; padding-left: 1rem; }
  ol { list-style: decimal; padding-left: 1rem; }
}
```

## Common surprises caused by Preflight

| Symptom | Cause | Fix |
|---|---|---|
| My `<h1>` is the same size as `<p>` | Headings unstyled | Add `text-3xl font-bold` utilities |
| Bullets disappeared from `<ul>` | Lists unstyled | Add `list-disc list-inside`, or wrap in `.prose` |
| Image is on its own line, breaking inline layout | Images are `display: block` | Add `inline` utility |
| Anchor isn't blue/underlined | Anchors inherit color/decoration | Style with utilities |
| Borders show up everywhere as currentColor | New v4 default border color | Set `@theme { --default-border-color: var(--color-gray-200); }` |
