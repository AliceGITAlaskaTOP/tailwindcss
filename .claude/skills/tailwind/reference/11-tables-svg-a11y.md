# Tables, SVG, Accessibility

## Tables

### Border collapse
- `border-collapse` — adjacent borders merge (default browser table look)
- `border-separate` — each cell keeps its own border (use with `border-spacing-*`)

### Border spacing (only with `border-separate`)
- `border-spacing-0` … `border-spacing-96` (spacing scale)
- Per axis: `border-spacing-x-*`, `border-spacing-y-*`
- Arbitrary `border-spacing-[7px]`

### Table layout
- `table-auto` — column widths based on content (default)
- `table-fixed` — equal columns, faster rendering, useful for predictable layout

### Caption side
- `caption-top` (default), `caption-bottom`

### Tailwind table recipe
```html
<table class="min-w-full divide-y divide-gray-200">
  <thead class="bg-gray-50">
    <tr>
      <th class="px-4 py-3 text-left text-xs font-medium uppercase tracking-wider text-gray-500">Name</th>
      <th class="px-4 py-3 text-left text-xs font-medium uppercase tracking-wider text-gray-500">Email</th>
    </tr>
  </thead>
  <tbody class="divide-y divide-gray-100 bg-white">
    <tr class="hover:bg-gray-50">
      <td class="px-4 py-3 text-sm">Alice</td>
      <td class="px-4 py-3 text-sm">a@b.com</td>
    </tr>
  </tbody>
</table>
```

### Sticky header
```html
<thead class="sticky top-0 bg-white">...</thead>
```

---

## SVG

### Fill
`fill-none`, `fill-current`, `fill-inherit`, `fill-transparent`, `fill-<color>` (`fill-blue-500/50`). Arbitrary `fill-[#fa0]`, `fill-(--my-color)`.

### Stroke
`stroke-none`, `stroke-current`, `stroke-<color>`. Arbitrary.

### Stroke width
`stroke-0`, `stroke-1`, `stroke-2`. Arbitrary `stroke-[1.5]`.

### Icon recipe
```html
<svg class="size-5 fill-current stroke-current stroke-1.5" viewBox="0 0 24 24">
  <path d="..." />
</svg>
```

Inheriting color from text: `text-blue-500` + `fill-current` makes the icon blue.

---

## Accessibility

### Screen-reader-only content
- `sr-only` — visually hidden but still announced
- `not-sr-only` — reverts (for `focus:not-sr-only` patterns like skip links)

```html
<!-- Skip link visible only on keyboard focus -->
<a href="#main" class="sr-only focus:not-sr-only focus:fixed focus:top-2 focus:left-2 focus:z-50 focus:rounded focus:bg-white focus:px-3 focus:py-2 focus:shadow">
  Skip to main content
</a>
```

### Forced colors (Windows high-contrast mode)
- `forced-color-adjust-auto` (default — browser overrides colors)
- `forced-color-adjust-none` (keep your colors)
- Variant `forced-colors:` lets you target the mode: `forced-colors:bg-[Canvas] forced-colors:text-[CanvasText]`

### Reduced motion
- `motion-safe:` only when `prefers-reduced-motion: no-preference`
- `motion-reduce:` when user opted out
- Pair with animations: `animate-spin motion-reduce:animate-none`

### Contrast preference
- `contrast-more:` when `prefers-contrast: more`
- `contrast-less:` when `prefers-contrast: less`

### Accessibility checklist for any UI Tailwind component
1. **Color contrast** — text vs background ≥ 4.5:1 (use `text-gray-700` not `text-gray-400` on white)
2. **Focus visible** — use `focus-visible:ring-2 focus-visible:ring-<brand>` not `focus:outline-none` alone
3. **Touch targets** — buttons/links ≥ 44px (`min-h-11 min-w-11` or `p-3` on size-5 icon)
4. **Semantic HTML first** — `<button>`, `<nav>`, `<main>`, `<header>` — not styled `<div>`s
5. **`aria-*` over class names** for state (use `aria-selected` + `aria-selected:bg-indigo-50`)
6. **Form labels** — every input needs a `<label>` (visible or `sr-only`)
7. **Dark mode contrast** — verify all `dark:` variants meet ratio
