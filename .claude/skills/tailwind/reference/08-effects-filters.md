# Effects & Filters

## Box shadow

### Preset sizes (v4 has finer scale)
| Class | Approx |
|---|---|
| `shadow-2xs` | very subtle 1px |
| `shadow-xs` | hairline + soft |
| `shadow-sm` | small (v3 default `shadow`) |
| `shadow-md` | medium |
| `shadow-lg` | large |
| `shadow-xl` | extra large |
| `shadow-2xl` | dramatic |
| `shadow-none` | none |

**v4 rename**: v3 `shadow` → v4 `shadow-sm`; v3 `shadow-sm` → v4 `shadow-xs`.

### Colored shadow
`shadow-<color>` (e.g., `shadow-indigo-500/50`). Useful for glow effects:
```html
<button class="bg-indigo-600 shadow-lg shadow-indigo-500/50">...</button>
```

### Custom
`shadow-[0_4px_30px_rgba(0,0,0,0.15)]`, `shadow-(--my-shadow)`.

## Inset shadow
- `inset-shadow-2xs`, `inset-shadow-xs`, `inset-shadow-sm`, `inset-shadow-none`
- Color: `inset-shadow-<color>`
- Common subtle inset: `inset-shadow-sm inset-shadow-white/10` for top highlight on buttons.

## Text shadow (v4)
`text-shadow-2xs`, `text-shadow-xs`, `text-shadow-sm`, `text-shadow-md`, `text-shadow-lg`, `text-shadow-none`. Color: `text-shadow-<color>`. Arbitrary `text-shadow-[0_2px_4px_rgba(0,0,0,0.3)]`.

## Opacity
`opacity-0`, `-5`, `-10`, `-15`, `-20`, `-25`, `-30`, `-40`, `-50`, `-60`, `-70`, `-75`, `-80`, `-90`, `-95`, `-100`. Arbitrary `opacity-[.67]`.

Prefer color/opacity (`bg-black/50`) over `opacity-*` when only one property needs transparency.

## Mix blend mode
`mix-blend-normal`, `-multiply`, `-screen`, `-overlay`, `-darken`, `-lighten`, `-color-dodge`, `-color-burn`, `-hard-light`, `-soft-light`, `-difference`, `-exclusion`, `-hue`, `-saturation`, `-color`, `-luminosity`, `-plus-darker`, `-plus-lighter`.

## Background blend mode
Same set with `bg-blend-*` prefix.

---

## Filters

All under the `filter` family — apply on any element. Stack freely.

### Blur
`blur-none`, `blur-xs`, `blur-sm`, `blur-md`, `blur-lg`, `blur-xl`, `blur-2xl`, `blur-3xl`. Arbitrary `blur-[2.5px]`.

### Brightness
`brightness-0`, `-50`, `-75`, `-90`, `-95`, `-100`, `-105`, `-110`, `-125`, `-150`, `-200`. Arbitrary.

### Contrast
`contrast-0/50/75/100/125/150/200`.

### Drop shadow (filter, not box-shadow — follows transparency)
`drop-shadow-xs/sm/md/lg/xl/2xl/none`. Color: `drop-shadow-<color>`. Best for SVG glow / cutout shapes.

### Grayscale
`grayscale` (= 100%), `grayscale-0`. Arbitrary `grayscale-[60%]`.

### Hue rotate
`hue-rotate-0/15/30/60/90/180`. Negative `-hue-rotate-30`. Arbitrary.

### Invert
`invert`, `invert-0`. Arbitrary `invert-[35%]`.

### Saturate
`saturate-0/50/100/150/200`.

### Sepia
`sepia`, `sepia-0`. Arbitrary.

### Disable all filters
`filter-none`. Or set individual: `blur-none`.

### Custom
`filter-[url(filters.svg#noise)]`, `filter-(--my-filter)`.

---

## Backdrop filter (filters applied to area behind element — for glass/frosted effects)

Same set with `backdrop-` prefix:
`backdrop-blur-*`, `backdrop-brightness-*`, `backdrop-contrast-*`, `backdrop-grayscale-*`, `backdrop-hue-rotate-*`, `backdrop-invert-*`, `backdrop-opacity-*`, `backdrop-saturate-*`, `backdrop-sepia-*`, `backdrop-filter-none`.

**Frosted glass recipe:**
```html
<div class="bg-white/30 backdrop-blur-md backdrop-saturate-150 border border-white/20 rounded-2xl p-6">
  ...
</div>
```

---

## Masks (v4)

CSS mask utilities (use to fade edges, create cutouts, etc.):

- `mask-clip-border` `mask-clip-padding` `mask-clip-content` `mask-clip-text` `mask-clip-no-clip`
- `mask-composite-add` `mask-composite-subtract` `mask-composite-intersect` `mask-composite-exclude`
- `mask-image-none`, `mask-[url('...')]`
- `mask-mode-alpha` `mask-mode-luminance` `mask-mode-match`
- `mask-origin-border` `mask-origin-padding` `mask-origin-content` `mask-origin-fill` `mask-origin-stroke` `mask-origin-view`
- `mask-position-*` (same set as `bg-position-*`)
- `mask-repeat-*` (same as bg-repeat)
- `mask-size-auto` `mask-size-cover` `mask-size-contain`
- `mask-type-alpha` `mask-type-luminance`

### Linear gradient mask shortcuts
`mask-linear-<dir/angle>`, with `mask-l-from-<value>`, `mask-l-to-<value>`. Similar for `mask-r-*`, `mask-t-*`, `mask-b-*`.

```html
<!-- Fade right edge -->
<div class="mask-r-from-50% mask-r-to-100%">...</div>

<!-- Custom mask image -->
<div class="mask-[linear-gradient(black,transparent)]">...</div>
```
