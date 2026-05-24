# Backgrounds & Borders

## Background color
`bg-<color>-<shade>`, `bg-transparent`, `bg-current`, `bg-inherit`, `bg-black`, `bg-white`.
Opacity: `bg-sky-500/50`, `bg-black/[37%]`.

## Background image
- `bg-none`
- `bg-[url('/img/hero.jpg')]`
- `bg-image-[url('...')]` (v4 explicit)

### Linear gradients (v4 — note `bg-linear-*` not `bg-gradient-*`)
- Direction shortcuts: `bg-linear-to-t`, `-to-tr`, `-to-r`, `-to-br`, `-to-b`, `-to-bl`, `-to-l`, `-to-tl`
- Angle: `bg-linear-45`, `bg-linear-90`, `bg-linear-[103deg]`
- Stops: `from-<color>`, `via-<color>`, `to-<color>`
- Stop positions: `from-10%`, `via-30%`, `to-90%` (or arbitrary `from-[15%]`)
- Interpolation modes: `bg-linear-to-r/oklch`, `/oklab` (default), `/srgb`, `/hsl`, `/longer`, `/shorter`, `/increasing`, `/decreasing`

### Radial gradients
- `bg-radial`
- `bg-radial-[at_50%_75%]`, `bg-radial-[circle_at_top_right]`
- `bg-radial-[<value>]` for full control

### Conic gradients
- `bg-conic`, `bg-conic-45`, `bg-conic-[from_90deg]`

### Examples
```html
<div class="h-32 bg-linear-to-r from-cyan-500 to-blue-500"></div>
<div class="h-32 bg-linear-65 from-purple-500 via-pink-500 to-amber-400"></div>
<div class="size-32 rounded-full bg-radial-[at_30%_30%] from-yellow-200 to-orange-600"></div>
<div class="size-32 rounded-full bg-conic from-rose-500 via-fuchsia-500 to-rose-500"></div>
<div class="h-32 bg-linear-to-r/oklch from-indigo-500 to-teal-400"></div>
```

## Background attachment
`bg-fixed`, `bg-local`, `bg-scroll`.

## Background clip
`bg-clip-border` (default), `bg-clip-padding`, `bg-clip-content`, `bg-clip-text` (use with `text-transparent` for gradient text).

```html
<h1 class="bg-linear-to-r from-pink-500 to-violet-600 bg-clip-text text-transparent text-5xl font-bold">
  Gradient title
</h1>
```

## Background origin
`bg-origin-border`, `bg-origin-padding`, `bg-origin-content`.

## Background position
`bg-top-left`, `bg-top`, `bg-top-right`, `bg-left`, `bg-center`, `bg-right`, `bg-bottom-left`, `bg-bottom`, `bg-bottom-right`. Arbitrary `bg-[center_top_-1rem]`.

## Background repeat
`bg-repeat` (default), `bg-no-repeat`, `bg-repeat-x`, `bg-repeat-y`, `bg-repeat-space`, `bg-repeat-round`.

## Background size
`bg-auto`, `bg-cover`, `bg-contain`. Arbitrary `bg-[length:200px_100px]`.

## Background blend mode
`bg-blend-normal`, `-multiply`, `-screen`, `-overlay`, `-darken`, `-lighten`, `-color-dodge`, `-color-burn`, `-hard-light`, `-soft-light`, `-difference`, `-exclusion`, `-hue`, `-saturation`, `-color`, `-luminosity`.

---

## Borders

### Width
- `border` (1px all sides), `border-0`, `border-2`, `border-4`, `border-8`
- Per side: `border-x-*`, `border-y-*`, `border-t-*`, `border-r-*`, `border-b-*`, `border-l-*`
- Logical: `border-s-*`, `border-e-*`
- Arbitrary `border-[3px]`

### Color
`border-<color>-<shade>`, `border-transparent`, `border-current`, opacity `border-red-500/30`.
Per side: `border-t-blue-500 border-b-red-500`.

**v4 default**: border color is `currentColor` (matches text). Set explicitly or override via `@theme { --default-border-color: var(--color-gray-200); }`.

### Style
`border-solid`, `border-dashed`, `border-dotted`, `border-double`, `border-hidden`, `border-none`.

### Border radius
| Class | Value |
|---|---|
| `rounded-none` | 0 |
| `rounded-xs` | 2px |
| `rounded-sm` | 4px |
| `rounded-md` | 6px |
| `rounded-lg` | 8px |
| `rounded-xl` | 12px |
| `rounded-2xl` | 16px |
| `rounded-3xl` | 24px |
| `rounded-4xl` | 32px |
| `rounded-full` | 9999px |

Side: `rounded-t-*`, `rounded-r-*`, `rounded-b-*`, `rounded-l-*`.
Logical: `rounded-s-*`, `rounded-e-*`.
Corner: `rounded-tl-*`, `rounded-tr-*`, `rounded-br-*`, `rounded-bl-*` (logical: `rounded-ss-*`, `-se-*`, `-ee-*`, `-es-*`).
Arbitrary `rounded-[14px]`.

## Outline (not the same as border — doesn't take space)
- Width: `outline`, `outline-0`, `outline-1`, `outline-2`, `outline-4`, `outline-8`
- Color: `outline-<color>`, opacity supported
- Style: `outline-solid`, `-dashed`, `-dotted`, `-double`, `-none`, `outline-hidden` (v4 replaces v3 `outline-none` — keeps element accessible)
- Offset: `outline-offset-0/1/2/4/8`, negative `-outline-offset-2`, arbitrary

## Divide (between siblings)
- `divide-x-*`, `divide-y-*` adds border between siblings
- Direction reverse: `divide-x-reverse`, `divide-y-reverse`
- Color: `divide-<color>`
- Style: `divide-solid/dashed/dotted/double/none`
```html
<ul class="divide-y divide-gray-200">
  <li class="py-3">A</li>
  <li class="py-3">B</li>
</ul>
```

## Ring (offset shadow used as border alternative — doesn't take layout space)
- `ring`, `ring-0`, `ring-1`, `ring-2`, `ring-4`, `ring-8`, arbitrary `ring-[3px]`
- Color: `ring-<color>`
- Offset (gap between element and ring): `ring-offset-0/1/2/4/8`, `ring-offset-<color>`
- Inset variant: `inset-ring`, `inset-ring-2`, `inset-ring-<color>`

**Common focus pattern (v4):**
```html
<button class="rounded bg-indigo-600 px-4 py-2 text-white
               focus:outline-none focus-visible:ring-2 focus-visible:ring-indigo-500 focus-visible:ring-offset-2">
  Save
</button>
```
