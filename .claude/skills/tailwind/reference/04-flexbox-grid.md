# Flexbox & Grid

## Flexbox

### Direction & wrap
| Class | CSS |
|---|---|
| `flex-row` `flex-row-reverse` | `flex-direction` |
| `flex-col` `flex-col-reverse` | `flex-direction: column[-reverse]` |
| `flex-wrap` `flex-wrap-reverse` `flex-nowrap` | `flex-wrap` |

### Grow / shrink / basis / flex
| Class | CSS |
|---|---|
| `grow` | `flex-grow: 1` |
| `grow-0` | `flex-grow: 0` |
| `grow-[2]` | arbitrary |
| `shrink` | `flex-shrink: 1` |
| `shrink-0` | `flex-shrink: 0` |
| `basis-*` | `flex-basis` (spacing scale + `auto`, `full`, `1/2`, `1/3`, fractions, `xs`–`7xl`) |
| `flex-1` | `flex: 1 1 0%` |
| `flex-auto` | `flex: 1 1 auto` |
| `flex-initial` | `flex: 0 1 auto` |
| `flex-none` | `flex: none` |
| `flex-[3_1_auto]` | arbitrary shorthand |

### Order
`order-1` … `order-12`, `order-first` (-9999), `order-last` (9999), `order-none`. Negative `-order-1`. Arbitrary.

### Alignment (works on flex AND grid containers)
| Axis | Class |
|---|---|
| `justify-content` (main axis) | `justify-start` `justify-end` `justify-center` `justify-between` `justify-around` `justify-evenly` `justify-stretch` `justify-normal` |
| `justify-items` (grid items main axis) | `justify-items-start/end/center/stretch` |
| `justify-self` | `justify-self-auto/start/end/center/stretch` |
| `align-items` (cross axis) | `items-start` `items-end` `items-center` `items-baseline` `items-stretch` |
| `align-content` (multi-line cross axis) | `content-start/end/center/between/around/evenly/stretch/baseline/normal` |
| `align-self` | `self-auto/start/end/center/stretch/baseline` |
| Shorthand both axes | `place-content-*`, `place-items-*`, `place-self-*` |

### Gap
`gap-0` … `gap-96` (spacing scale), `gap-x-*`, `gap-y-*`. Arbitrary `gap-[7px]`.

### Common flex patterns
```html
<!-- Center anything -->
<div class="flex items-center justify-center min-h-screen">...</div>

<!-- Split layout (logo left, actions right) -->
<header class="flex items-center justify-between p-4">
  <Logo />
  <nav class="flex gap-4">...</nav>
</header>

<!-- Sidebar + content -->
<div class="flex">
  <aside class="w-64 shrink-0">...</aside>
  <main class="flex-1 min-w-0">...</main>
</div>

<!-- Responsive stack → row -->
<div class="flex flex-col md:flex-row gap-4">
  <div class="flex-1">...</div>
  <div class="flex-1">...</div>
</div>
```

---

## Grid

### Template columns / rows
| Class | CSS |
|---|---|
| `grid-cols-1` … `grid-cols-12` | `repeat(N, minmax(0, 1fr))` |
| `grid-cols-none` | `none` |
| `grid-cols-subgrid` | `subgrid` |
| `grid-cols-[200px_1fr_100px]` | arbitrary |
| `grid-cols-(--my-cols)` | CSS var |

Same for `grid-rows-1` … `grid-rows-6`, `grid-rows-none`, `grid-rows-subgrid`, arbitrary.

### Span / start / end
- `col-span-1` … `col-span-12`, `col-span-full`, `col-auto`
- `col-start-1` … `col-start-13`, `col-end-1` … `col-end-13`
- `row-span-1` … `row-span-6`, `row-span-full`
- `row-start-1` … `row-start-7`, `row-end-1` … `row-end-7`
- Arbitrary: `col-span-[3]`, `col-start-[2]`

### Auto-flow / auto sizing
- `grid-flow-row`, `grid-flow-col`, `grid-flow-dense`, `grid-flow-row-dense`, `grid-flow-col-dense`
- `auto-cols-auto` `auto-cols-min` `auto-cols-max` `auto-cols-fr` (same for `auto-rows-*`). Arbitrary `auto-cols-[minmax(0,2fr)]`.

### Gap
Same `gap-*` / `gap-x-*` / `gap-y-*` as flex.

### Common grid patterns
```html
<!-- Card grid, responsive -->
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
  ...cards...
</div>

<!-- 12-col layout -->
<div class="grid grid-cols-12 gap-4">
  <aside class="col-span-12 md:col-span-3">...</aside>
  <main  class="col-span-12 md:col-span-9">...</main>
</div>

<!-- Holy grail -->
<div class="grid min-h-screen grid-rows-[auto_1fr_auto]">
  <header>...</header>
  <main>...</main>
  <footer>...</footer>
</div>

<!-- Image cover + caption -->
<figure class="grid grid-rows-[1fr_auto]">
  <img class="row-span-1 w-full object-cover" />
  <figcaption>...</figcaption>
</figure>

<!-- Auto-fit responsive (no breakpoints) -->
<div class="grid grid-cols-[repeat(auto-fit,minmax(220px,1fr))] gap-4">...</div>

<!-- Subgrid (align child rows to parent grid) -->
<div class="grid grid-cols-3 gap-4">
  <div class="col-span-3 grid grid-cols-subgrid gap-4">
    <div>A</div><div>B</div><div>C</div>
  </div>
</div>
```
