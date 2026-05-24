# Core Concepts

## 1. Utility classes

Compose styles by combining single-purpose utilities. No naming, no abstraction layer.

```html
<button class="rounded-md bg-indigo-600 px-4 py-2 text-sm font-medium text-white hover:bg-indigo-500">
  Save
</button>
```

When the same class set repeats, extract a component (React/Vue/Svelte) — **not** a CSS class. If you must extract CSS, use `@apply` inside `@layer components`.

## 2. State variants

Prefix any utility with a variant. Variants stack (`md:dark:hover:bg-red-500`). Variant specificity is equal — source order wins on conflicts.

### Interactive
`hover:`, `focus:`, `focus-within:`, `focus-visible:`, `active:`, `visited:`, `target:`

### Pseudo-elements (auto-add `content: ''` for before/after)
`before:`, `after:`, `first-letter:`, `first-line:`, `placeholder:`, `file:`, `marker:`, `selection:`, `backdrop:`

### Structural
`first:`, `last:`, `only:`, `odd:`, `even:`, `first-of-type:`, `last-of-type:`, `only-of-type:`, `empty:`, `nth-[3]:`, `nth-[3n+1]:`, `nth-last-[2]:`, `nth-of-type-[2]:`

### Form states
`disabled:`, `enabled:`, `required:`, `optional:`, `checked:`, `indeterminate:`, `default:`, `valid:`, `invalid:`, `user-valid:`, `user-invalid:`, `in-range:`, `out-of-range:`, `placeholder-shown:`, `autofill:`, `read-only:`

### Parent/sibling targeting
```html
<!-- group: child reacts to parent state -->
<div class="group">
  <img class="group-hover:opacity-50" />
</div>

<!-- named group (nested) -->
<li class="group/item">
  <a class="group-hover/item:underline">link</a>
</li>

<!-- peer: sibling reacts to prior sibling -->
<input class="peer" required />
<p class="peer-invalid:text-red-500">Required</p>

<!-- named peer -->
<input class="peer/email" />
<span class="peer-focus/email:text-blue-600">...</span>
```

### `has-*` and `not-*`
```html
<label class="has-checked:bg-indigo-50">
  <input type="checkbox" /> Subscribe
</label>

<button class="hover:not-focus:bg-indigo-700">Save</button>
```

### Child selectors
- `*:` → direct children (`*:rounded-full`)
- `**:` → all descendants (`**:data-avatar:size-12`)

### Attribute selectors
```html
<div aria-checked="true" class="aria-checked:bg-sky-700">...</div>
<div class="aria-[sort=ascending]:bg-blue-100">...</div>
<div data-active class="data-active:border-purple-500">...</div>
<div data-size="lg" class="data-[size=lg]:p-8">...</div>
<div class="ltr:ml-3 rtl:mr-3">...</div>
<details class="open:bg-gray-100">...</details>
```

### Media/feature queries
| Variant | Meaning |
|---|---|
| `sm: md: lg: xl: 2xl:` | Breakpoint (min-width) |
| `max-sm:` etc. | Max-width |
| `@sm: @md:` | Container query (needs `@container` parent) |
| `dark:` | `prefers-color-scheme: dark` (or class strategy) |
| `motion-safe:` / `motion-reduce:` | `prefers-reduced-motion` |
| `contrast-more:` / `contrast-less:` | `prefers-contrast` |
| `forced-colors:` | High-contrast mode |
| `pointer-fine:` / `pointer-coarse:` | Input device |
| `portrait:` / `landscape:` | Orientation |
| `print:` | Print media |
| `supports-[display:grid]:` | `@supports` query |

### Arbitrary variants
```html
<div class="[&.is-open]:rotate-180">...</div>
<div class="[&_p]:mt-4">all p descendants</div>
<div class="[@supports(display:grid)]:grid">...</div>
```
Underscores in selectors = spaces.

### Important modifier (v4 — at END)
```html
<div class="bg-red-500!">forced</div>
```

## 3. Responsive design

Mobile-first. Plain = all screens. Prefix = that breakpoint and up.

Default breakpoints:
| | rem | px | Media |
|---|---|---|---|
| `sm` | 40rem | 640 | `@media (width >= 40rem)` |
| `md` | 48rem | 768 | `@media (width >= 48rem)` |
| `lg` | 64rem | 1024 | `@media (width >= 64rem)` |
| `xl` | 80rem | 1280 | `@media (width >= 80rem)` |
| `2xl` | 96rem | 1536 | `@media (width >= 96rem)` |

### Patterns
```html
<!-- correct mobile-first -->
<div class="text-center sm:text-left">

<!-- target range with max-* -->
<div class="md:max-lg:flex">  <!-- 768–1024 only -->

<!-- arbitrary breakpoint -->
<div class="min-[420px]:text-xl max-[640px]:bg-red-100">
```

### Custom breakpoints
```css
@theme {
  --breakpoint-xs: 30rem;
  --breakpoint-3xl: 120rem;
  --breakpoint-2xl: initial; /* remove default */
}
```

### Container queries
```html
<div class="@container">
  <div class="flex flex-col @md:flex-row">
    <!-- @md fires when *container* width ≥ md -->
  </div>
</div>

<!-- named container -->
<div class="@container/sidebar">
  <div class="@sm/sidebar:hidden">...</div>
</div>

<!-- arbitrary container size -->
<div class="@min-[475px]:flex-row @max-[960px]:bg-blue-100">

<!-- container query units -->
<div class="@container">
  <div class="w-[50cqw]">half of container width</div>
</div>
```

Custom container sizes:
```css
@theme { --container-8xl: 96rem; }
```

## 4. Dark mode

### Default: follows OS (`prefers-color-scheme`)
```html
<div class="bg-white text-gray-900 dark:bg-gray-900 dark:text-white">
```

### Manual class toggle (v4)
```css
@import "tailwindcss";
@custom-variant dark (&:where(.dark, .dark *));
```
```html
<html class="dark">...</html>
```

### Data attribute toggle
```css
@custom-variant dark (&:where([data-theme=dark], [data-theme=dark] *));
```

### Toggle script
```js
// Initial
document.documentElement.classList.toggle(
  'dark',
  localStorage.theme === 'dark' ||
  (!('theme' in localStorage) && matchMedia('(prefers-color-scheme: dark)').matches)
)
// On toggle button click
localStorage.theme = 'dark'
document.documentElement.classList.add('dark')
```

## 5. Theme variables

v4 config lives in CSS via `@theme`. Each `--<namespace>-<name>` token auto-generates the matching utilities.

### All namespaces
| Namespace | Generates |
|---|---|
| `--color-*` | `bg-`, `text-`, `border-`, `ring-`, `fill-`, `stroke-`, `outline-`, `caret-`, `accent-`, `shadow-`, `from-`, `via-`, `to-`, `decoration-` |
| `--font-*` | `font-sans`, `font-serif`, `font-mono` (family) |
| `--text-*` | Font size (`text-xs`–`text-9xl`, custom) |
| `--font-weight-*` | `font-thin`–`font-black` |
| `--tracking-*` | `tracking-tight`, `tracking-wide`, ... |
| `--leading-*` | `leading-none`, `leading-relaxed`, ... |
| `--breakpoint-*` | `sm:`, `md:`, ... variants |
| `--container-*` | `@sm:` variants & `max-w-md` sizes |
| `--spacing` (single token) | Everything spacing-based: `p-`, `m-`, `gap-`, `w-`, `h-`, etc. |
| `--radius-*` | `rounded-*` |
| `--shadow-*` | `shadow-*` |
| `--inset-shadow-*` | `inset-shadow-*` |
| `--drop-shadow-*` | `drop-shadow-*` (filter) |
| `--blur-*` | `blur-*` |
| `--perspective-*` | `perspective-*` |
| `--aspect-*` | `aspect-*` |
| `--ease-*` | `ease-*` |
| `--animate-*` | `animate-*` |
| `--default-*` | `--default-transition-duration`, `--default-font-family`, etc. |

### Example
```css
@import "tailwindcss";
@theme {
  --color-brand: oklch(0.6 0.18 240);
  --color-brand-dark: oklch(0.4 0.18 240);
  --font-display: "Satoshi", sans-serif;
  --text-tiny: 0.625rem;
  --breakpoint-3xl: 120rem;
  --radius-4xl: 2rem;
  --ease-fluid: cubic-bezier(0.3, 0, 0, 1);
}
```

→ generates `bg-brand`, `text-brand-dark`, `font-display`, `text-tiny`, `3xl:`, `rounded-4xl`, `ease-fluid`.

### Override / remove defaults
```css
@theme {
  --color-gray-50: oklch(0.984 0.003 247.858);  /* override one */
  --color-*: initial;                            /* wipe all colors */
  --color-white: #fff;                           /* then add yours */
}
```

### Reading theme vars in CSS
```css
.btn { background-color: var(--color-brand); }
.muted { color: --alpha(var(--color-gray-950) / 60%); }
.gap-half-spacing { gap: --spacing(0.5); }
```

### Reading theme vars in JS
```js
getComputedStyle(document.documentElement).getPropertyValue('--color-brand')
```

## 6. Colors

### Default palettes (24)
`red, orange, amber, yellow, lime, green, emerald, teal, cyan, sky, blue, indigo, violet, purple, fuchsia, pink, rose, slate, gray, zinc, neutral, stone` (v4 added `taupe, mauve, mist, olive` in latest)
Shades: `50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950`
Plus: `black`, `white`, `transparent`, `current`, `inherit`

### Color-applying utilities
`bg-`, `text-`, `border-`, `decoration-`, `outline-`, `ring-`, `inset-ring-`, `shadow-`, `inset-shadow-`, `accent-`, `caret-`, `fill-`, `stroke-`, `from-`, `via-`, `to-`, `divide-`, `placeholder-`

### Opacity modifier
```html
<div class="bg-sky-500/50">  <!-- 50% alpha -->
<div class="text-black/70">
<div class="border-pink-500/[37%]">  <!-- arbitrary -->
<div class="bg-blue-500/(--my-alpha)">  <!-- CSS var -->
```

## 7. Adding custom styles

### Arbitrary values
```html
<div class="top-[117px] bg-[#bada55] text-[22px]">
<div class="grid-cols-[200px_1fr_100px]">
<div class="[mask-type:luminance] hover:[mask-type:alpha]">
<div class="fill-(--my-brand)">  <!-- CSS var -->
```

### `@layer base` — global element styles
```css
@layer base {
  h1 { font-size: var(--text-3xl); font-weight: 700; }
  a  { color: var(--color-blue-600); }
}
```

### `@layer components` — reusable composite classes (override-able by utilities)
```css
@layer components {
  .btn {
    @apply inline-flex items-center rounded-md bg-indigo-600 px-4 py-2 text-white;
  }
}
```

### `@utility` — custom single-purpose utilities
```css
@utility content-auto { content-visibility: auto; }

/* functional, from theme */
@theme { --tab-size-2: 2; --tab-size-4: 4; }
@utility tab-* { tab-size: --value(--tab-size-*); }

/* functional, accepts arbitrary integers */
@utility tab-* { tab-size: --value([integer]); }
```

### `@custom-variant`
```css
@custom-variant theme-midnight (&:where([data-theme=midnight] *));
```
```html
<div class="theme-midnight:bg-black">...</div>
```

### Plugins (legacy JS)
```css
@plugin "@tailwindcss/typography";
@plugin "@tailwindcss/forms";
```

## 8. Detecting classes in source files

v4's Oxide engine auto-scans every file in your project — no `content: [...]` config needed. If a class is in a non-scanned location (vendored libs), add:

```css
@source "../node_modules/@my-company/ui-lib";
@source "../legacy-templates/**/*.html";
```

Negate:
```css
@source not "../legacy/**";
```

## 9. Directives & functions cheat sheet

| Directive | Purpose |
|---|---|
| `@import "tailwindcss";` | Load Tailwind (base + theme + utilities) |
| `@theme { ... }` | Define design tokens |
| `@source "path";` | Extra source globs for class detection |
| `@utility name-* { ... }` | Define a custom utility |
| `@custom-variant name (...);` | Define a custom variant |
| `@variant dark { ... }` | Apply Tailwind variant inside custom CSS |
| `@apply class1 class2;` | Inline existing utilities into custom CSS |
| `@reference "path";` | Bring theme into scoped/module CSS without duplicating output |
| `@layer base|components|utilities { ... }` | Place rules in a specific cascade layer |
| `@config "./tailwind.config.js";` | Load legacy v3 JS config |
| `@plugin "name";` | Load legacy JS plugin |

| Function | Purpose |
|---|---|
| `--alpha(<color> / <pct>)` | Adjust alpha of a color expression |
| `--spacing(<n>)` | `calc(var(--spacing) * <n>)` |
| `theme(spacing.4)` | Legacy v3 theme accessor (avoid in v4 — use CSS vars) |
